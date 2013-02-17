NFluent overview
==============

NFluent provides some extension methods for a __fluent .NET TDD experience__ based on simple Assert.That(bool condition) statements.

__NFluent will make your tests__:
+ __fluent to write__: with auto completion support
+ __fluent to read__: very close to plain English, making it easier for non-technical people to read test code.
+ __fluent to troubleshoot__: every failing extension method of the NFluent library throws Exception with clear message status to ease your TDD experience.
+ __less error-prone__: indeed, no more confusion about the order of the "expected" and "actual" values.

NFluent is __highly inspired by the awesome Java FEST Fluent__ assertion/reflection library (http://fest.easytesting.org/)


Disclaimer
----------
__NFluent is not coupled to any .NET unit test framework. It is fully designed to work in collaboration with your favorite one.__

With NUnit for instance, you can simply use all the NFluent method extensions from any NUnit Assert.That(bool condition) statement.

If you are using another .NET unit tests framework which don't provide such nice and simple Assert.That() bootstraping method (e.g. xUnit), you can use the one gracefully provided by the NFluent library. 

Usage sample
------------

With NFluent, you can write some assertions like this:
	
	var integers = new int[] { 1, 2, 3, 4, 5, 666 };
    Assert.That(integers.ContainsExactly(1, 2, 3, 4, 5, 666));

	var guitarHeroes = new[] { "Hendrix", "Paco de Lucia", "Django Reinhardt", "Baden Powell" };
    Assert.That(guitarHeroes.ContainsExactly("Hendrix", "Paco de Lucia", "Django Reinhardt", "Baden Powell"));

(note: the Assert.That is here part of the NUnit library)

with NFluent, you can also write something like this:

	 var enumerable = new List<Person>
                                 {
                                     new Person { Name = "Thomas", Age = 38 },
                                     new Person { Name = "Achille", Age = 10, Nationality = Nationality.French },
                                     new Person { Name = "Anton", Age = 7, Nationality = Nationality.French },
                                     new Person { Name = "Arjun", Age = 7, Nationality = Nationality.Indian }
                                 };

     Assert.That(enumerable.Properties("Name").ContainsExactly("Thomas", "Achille", "Anton", "Arjun"));
     Assert.That(enumerable.Properties("Age").ContainsExactly(38, 10, 7, 7));
     Assert.That(enumerable.Properties("Nationality").ContainsExactly(Nationality.Unknown, Nationality.French, Nationality.French, Nationality.Indian));

	 // more fluent than the following classical NUnit way, isn't it? 
     CollectionAssert.AreEquivalent(enumerable.Properties("Age"), new[] { 38, 10, 7, 7 });

     // NFluent relies intensively on intellisense to make you more productive in your day to day TDD

     // java version (FEST fluent assert)
     // assertThat(inn.getItems()).onProperty("name").containsExactly("+5 Dexterity Vest", "Aged Brie", "Elixir of the Mongoose", "Sulfuras, Hand of Ragnaros", "Backstage passes to a TAFKAL80ETC concert", "Conjured Mana Cake");
        

- - -

*author:* thomas@pierrain.net
*date:* February 6th 2013
