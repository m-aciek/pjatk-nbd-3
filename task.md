* Jedna osoba znajdująca się w bazie;


    > db.people.findOne()

* Jedna kobieta narodowości chińskiej;


    > db.people.findOne({"nationality": "China", "sex": "Female"})
    
* Lista mężczyzn narodowości niemieckiej;


    > db.people.find({"nationality": "Germany", "sex": "Male"})

* Lista wszystkich osób znajdujących się w bazie o wadze z przedziału <68, 71.5);


    > db.people.find({"weight": { $gte :  "68", $lt : "71.5"}})


* Lista imion i nazwisk wszystkich osób znajdujących się w bazie oraz miast, w których mieszkają, ale tylko dla osób urodzonych w XXI wieku;


    > db.people.find({birth_date: { $gte :  "2001-01-01T00:00:00Z"}}, {first_name: 1, last_name: 1, location: {city: 1}, _id: 0})

* Dodaj siebie do bazy, zgodnie z formatem danych użytych dla innych osób (dane dotyczące karty kredytowej, adresu zamieszkania i wagi mogą być fikcyjne);


    > db.people.insertOne(
    {sex: "Male", first_name: "Maciej", last_name: "Olko", job: "Python developer", email: "private@example.com", location: {city: "Warsaw", address: {streetname: "Piękna", streetnumber: "1"}}, "description": "lorem ipsum", height: "187", weight: "70", birth_date: "1991-01-01T00:00:00Z", nationality: "Poland", credit: [{type: "switch", number: 0000, currency: "PLN", balance: "3.04"}]}
    ) 

* Usuń z bazy osoby o wzroście przekraczającym 190;


    > db.people.deleteMany({height: {$gt: "190"}})

* Zastąp nazwę miasta „Moscow” przez „Moskwa” u wszystkich osób w bazie;


    > db.people.updateMany({"location.city": "Moscow"}, {$set: {"location.city": "Moskwa"}})

9. Dodaj do wszystkich osób o imieniu Antonio własność „hobby” o wartości „pingpong”;


    > db.people.updateMany({first_name: "Antonio"}, {$set: {hobby: "pingpong"}})

10. Usuń u wszystkich osób o zawodzie „Editor” własność „email”.


    > db.people.updateMany({job: "Editor"}, {$unset: {email: 1}})
    