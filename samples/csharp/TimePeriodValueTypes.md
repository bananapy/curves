# Time Period Value Types
This markdown file provides interactive documentation using [Try .NET](https://dotnet.microsoft.com/platform/try-dotnet). If you haven't already, follow the instructions on [README](README.md) to set up and run.

The namespace Cmdty.TimePeriodValueTypes contains a set of types used to represent a time period for specific granularity. Examples of such types include Month, Quarter, HalfHour and Hour, but many others are also present.

These types are used extensively within the Cmdty library to represent the delivery periods for traded commodities. However, there is nothing commodity-specific within the Time Period Value Types API, and hence these types could be used in many other non-commodity business contexts.


### Creating Instances
As well as being able to create instances using constructors, many types have helper static factory methods as shown for the Month and Quarter types below.
All Time Period types also have a FromDateTime static methods for
converting instances of .NET System.DateTime to time period types.
```cs --region creating --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```

### Parsing and Formatting
The ToString method is overridden on all types to provide a human readable text representation.
All types also have a static Parse method which can create an intance 
from this text representation. The ToString and Parse methods can be used in a round-trip fashion.

Some of the types also implement IFormattable which means an additional override of the ToString method is provided which includes parameters for a format string and format provider. This is demonstrated below for the Hour type.
```cs --region parsing_formatting --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```

### Comparing Instances
All time period types implement IComparable\<T\> and so have the CompareTo method for strongly typed comparison between instances of the same type.

For convenience, the comparison and equality operators are also overloaded for all time period types.
```cs --region comparing --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```

### Offsetting Instances
The Offset method allows the calculation of time period instances a relative number of time periods before or after a specific instance.

The OffsetFrom method performs the inverse operation, calculating the integer number of periods difference between the current instance and another instance.
```cs --region offsetting --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```

The same logic as the instance methods Offset and OffsetFrom from can be called using the + and - operators respectively. The increment and decrement operators, ++ and -- are also provide for all time period types.

```cs --region offset_operators --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```

### Converting Between Granularities
Convertion between different granularity time periods can be achieved using the methods First\<T\> and Last\<T\>.
```cs --region converting_granularity --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```

### Expanding
The Expand\<T\> method can be use to expand a time period into a collection of instances of higher granularity time period type, as is shown in the example below which calculates all the months in Q2-19.
```cs --region expanding --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```

### Range of Valid Values
All time period types have static properties give information on the valid range for each time period type.
```cs --region time_period_ranges --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```

### Extension Methods
Extension method provide extra useful functionality, such as the EnumerateTo and EnumerateWeekdaysDays methods shown in the example below.
```cs --region extension_methods --source-file ./Cmdty.Curves.Samples.TimePeriodValueTypes/Program.cs --project ./Cmdty.Curves.Samples.TimePeriodValueTypes/Cmdty.Curves.Samples.TimePeriodValueTypes.csproj
```
