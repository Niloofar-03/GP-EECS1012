class Order {
    private ArrayList<Child> children;

    public Order() {
        this.children = new ArrayList<>();
    }

    public void addChildtoOrder(Child child) {
        if (children.size() < 5) { 
            children.add(child);
        } 
    }

    public void removeChildfromOrder(Child child) {
         children.remove(child); 
    }

    public Child[] getChilds() {
        return children.toArray(new Child[0]); 
    }
    public int getNumofChilds() {
        return children.size(); 
    }
    @Override
    public String toString() {
        return "The order contains "+children.size()+" Childs";
    }

}


class Child {
    private String ChildName;
    private int ChildAge;
    private Toy[] ChildToy;

    public Child() {
        this.ChildName = "";
        this.ChildAge = 0;
        this.ChildToy = new Toy[0]; 
    }

   
    public Child(String ChildName, int ChildAge, Toy[] ChildToy) {
        this.ChildName = ChildName;
        this.ChildAge = ChildAge;
        if (ChildToy != null) {
            this.ChildToy = new Toy[ChildToy.length];
            for (int i = 0; i < ChildToy.length; i++) {
                this.ChildToy[i] = new Toy(ChildToy[i]); 
            }
        } else {
        	if (ChildToy == null) {
            this.ChildToy = new Toy[0]; 
        }
       }
    }


    public Child(Child other) {
        this.ChildName = other.ChildName;
        this.ChildAge = other.ChildAge;
        this.ChildToy = new Toy[other.ChildToy.length];
        for (int i = 0; i < other.ChildToy.length; i++) {
            this.ChildToy[i] = new Toy(other.ChildToy[i]);
        }
    }

    public void setChildAge(int ChildAge) {
        this.ChildAge = ChildAge;
    }

    public int getChildAge() {
        return ChildAge;
    }

    public void setToys(Toy[] ChildToy) {
        if (ChildToy != null) {
            this.ChildToy = new Toy[5];
            for (int i = 0; i < 5; i++) {
                this.ChildToy[i] = new Toy(ChildToy[i]); 
            }
        } else {
        	 if (ChildToy == null) {
            this.ChildToy = new Toy[0]; 
        }
       }
    }

    public void setChildName(String ChildName) {
        this.ChildName = ChildName;
    }

    public String getChildName() {
        return ChildName;
    }

    public Toy[] getChildToy() {
    	
        return (ChildToy==null || ChildToy.length==0)?null:ChildToy; 
    	
    }

    public int getNumberofToys() {
        return ChildToy.length; 
    }

    public void addToy(Toy toy) {
        if (getNumberofToys() < 5) { 
            Toy[] newToys = new Toy[getNumberofToys() + 1];
          
            for (int i = 0; i < ChildToy.length; i++) {
                newToys[i] = ChildToy[i];
            }
      
            newToys[getNumberofToys()] = toy;
            ChildToy = newToys; 
        }
    }


    public void disposeToys() {
        ChildToy = new Toy[0]; 
    }

    public void donate(Child recipient) {
        if (recipient != this && getNumberofToys() > 0) { 
            for (Toy toy : getChildToy()) {
                if (recipient.getNumberofToys() < 5) {
                    recipient.addToy(toy);
                }
            }
            disposeToys();
        }
    }

    public void addToys(Toy[] toys) {
    	 if (toys != null) { 
    	        for (int i = 0; i < toys.length; i++) { 
    	            addToy(toys[i]); 
    	        }
    	    }
    }

    public String getChildInformation() {
        return "Child [" + ChildName + "] of age <" + ChildAge + "> has (" + getNumberofToys() + ") toys";
    }

    @Override
    public String toString() {
        return getChildInformation();
    }
}





class Toy {
 private int ToyID;
 private String ToyName;
 private int ToyQuantity;
 private double ToyPrice;

 public Toy(Toy other) {
	    this.ToyID = other.ToyID;
	    this.ToyName = other.ToyName;
	    this.ToyQuantity = other.ToyQuantity;
	    this.ToyPrice = other.ToyPrice;
	}


public Toy(int ToyID, String ToyName, int ToyQuantity, double ToyPrice) {
	this.ToyID=ToyID;
	this.ToyName=ToyName;
	this.ToyQuantity=ToyQuantity;
	this.ToyPrice=ToyPrice;
}

public void setToyName(String ToyName) {
	this.ToyName=ToyName;
}
public String getToyName() {
	return ToyName;
}


public void setToyID(int ToyID) {
	this.ToyID=ToyID;
}
	
public int getToyID() {
	return ToyID;
}	
public void setToyQuantity(int ToyQuantity) {
	this.ToyQuantity=ToyQuantity;
}
public int getToyQuantity() {
	return ToyQuantity;
}

public void setToyPrice(double ToyPrice) {
	this.ToyPrice=ToyPrice;
}
public double getToyPrice() {
	
	return ToyPrice ;
}


public String getToyInformation() {
	
	return "Toy("+ToyID+","+ToyName+"), quantity("+ToyQuantity+") with $( "+String.format("%.2f", ToyPrice)+")/toy";
}


}


