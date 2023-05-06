# dynasearch

Dynasearch is a Java module that provides a generic implementation for full-text search on any iterable collection. It allows users to search for text in one or more properties of the items in the collection.

## Features

- Perform full-text search on an iterable collection
- Search for text in one or more properties of the items
- Case-insensitive search
- Supports searching multiple terms within a property
- Easily customizable with property accessors

## Usage

1. Create an iterable collection of objects that you want to search.
2. Implement the `PropertyAccessor` interface to specify how to access the properties to be searched.
3. Create an instance of the `GenericTextSearch` class, passing in the iterable collection and the list of property accessors.
4. Use the `search` method to perform the search, providing the search text.
5. Receive the search results as a list of matching items.

Here's an example usage:

```java

List<Person> people = Arrays.asList(
        new Person("John", "Doe", "Engineer"),
        new Person("Jane", "Smith", "Manager"),
        new Person("Bob", "Johnson", "Engineer"),
        new Person("Alice", "Doe", "Designer")
);

// initialize
Dynasearch<Person> dynasearch = new Dynasearch<Person>(Person.class, people);

// use
List<Person> searchResults = dynasearch.search("John");


// Print the search results
for (Person person : searchResults) {
    System.out.println(person.getFirstName() + " " + person.getLastName() + " - " + person.getJobTitle());
}

// returns
// John Doe - Engineer
// Bob Johnson - Engineer
```

## Case Sensitivity

The search performed by Dynasearch is case-insensitive. Both the search text and the property values are converted to lowercase for comparison.
