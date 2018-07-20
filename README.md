# Java_EE_Udemy27
Java Persistence Unit and Relational Databases - Injecting an Entity Manager + Persisting a Passenger object into the database
This tutorial llooked at injecting an Entity Manager associated with the Persistence Unit and then Persisting a passenger object into the database.
I created a Session Bean Called PassengerService which linked back to the persistence.xml file with the following code:
      @PersistenceContext(unitName="airline")
      private EntityManager em;
    
      		public void addPassenger(Passenger p) {
    	
    	  	em.persist(p);
        
Then i created a Servlet called AddPassenger which linked to Passenger object with this code:
    @EJB
	  PassengerService ps;
    
Inside the doGet method i created a Passenger object, printed to the console and saved to teh database:
    Passenger p = new Passenger();
		
		p.setFirstName("Catherine");
		p.setLastName("Lacoste");
		
		Calendar cal = Calendar.getInstance();
		
		cal.set(Calendar.YEAR, 1970);
		cal.set(Calendar.MONTH, 3);
		cal.set(Calendar.DAY_OF_MONTH, 12);
		
		Date dob = cal.getTime();
		
		p.setDob(dob);
		
		p.setGender(Gender.Female);
		
		p.setFlightClass(FlightClass.Coach);
		
		System.out.println(p);
		
		ps.addPassenger(p);
    
There were a few odd issues with the database, it was all running and pinged but would not save the passenger object. Two days of trying different
things including restarting everything and when i started the servers today it worked! Coding is great sometimes!
