# Ember+ SDK Release Notes #



## Ember+ SDK 1.6.2 Release Notes ##

### Overview ###

Version 1.6.2 of the Ember+ SDK is a maintenance release that fixes an
important oversight in version 1.6.0 with regard to the correct spelling of the newly introduced "schemaIdentifiers" attribute.

In addition to this functional change this release increases stability and addresses a few performance problems. All users of the 1.6.0 version are encouraged to update to this release as soon as possible.

### Fixes ###
  * Updated DTD version implemented by the various libraries to 2.31 which includes a minor change to the naming of the schemaIdentifier attribute.<br />Please note that this requires a small change to client code that uses the accessors, because the spelling has been changed from the singular form "schemaIdentifier" to the plural form "schemaIdentifiers".
  * Fixed potential memory leaks during decoding in `DomReader`.
  * Optimized the equality comparison of two type erased iterator instances, yielding a massive performance improvement in typical loop constructs.
  * Corrected the signedness of a few temporary variables and integral constants used in the implementation.
  * Removed extraneous semicolons that caused compiler warnings on high warning-levels.
  * Removed obsolete entries from the Doxygen configuration and corrected wrong output directories in the Doxygen configuration.

### Additions ###
  * Added a method called compliesWithSchema which tests whether a schema is part of the schema identifier collection of a node, parameter or matrix.


## Ember+ SDK 1.6.0 Release Notes ##

### Overview ###

Version 1.6.0 of the Ember+ SDK is a feature release that introduces the new Schema extension to the GLOW DTD.

Apart from this new feature this release also contains numerous fixes and stability improvements.

### Additions ###
  * Added a Ruby script that converts the premake4 generated VS2012 solution to VS2013 because the automated conversion no longer works reliable  strange licensing reasons.
  * Added traits to determine the property type from a GLOW type.
  * Added `libember::ber::ObjectIdentifier::push_back(..)` and `libember::ber::ObjectIdentifier::push_front(..)` to allow building a path iteratively. Changed the underlying container to `std::deque<..>` in order to support `push_front(..)`.
  * Added `libember::ber::ObjectIdentifier::back()` to access the last element of the OID.
  * Added explicit constructor taking an argument of type value\_type to some of the enum-wrappers (`CommandType`, `MessageType`, `Dtd`). `PackageFlag` and `Byte` already have a non-explicit constructor taking an argument of type `value_type`.
  * Added equality operators for some of the enum-wrapper types.

### Fixes ###
  * Fixed [issue #13](https://code.google.com/p/ember-plus/issues/detail?id=#13), by changing the visibility of the default constructor of `GlowRootElementCollection` and setting the root tag in the default constructor.
  * Fixed [issue #14](https://code.google.com/p/ember-plus/issues/detail?id=#14) by replacing the standard container with a more suitable alternative and storing the stack elements by value.
  * Fixed [issue #15](https://code.google.com/p/ember-plus/issues/detail?id=#15) by Replacing C++11 specific constructs in libember with their C++03 equivalents and changing the C++ language standard on non-Windows platforms from C++11 to C++03.
  * Fixed [issue #17](https://code.google.com/p/ember-plus/issues/detail?id=#17), pass (type-erased) iterator by const-reference, because copying it is expensive.
  * Fixed macro to generate type-traits, which was causing errors under GCC.
  * Fixed `GlowTupleItemDescription::type()` always returning `ParameterType::None`.
  * Fixed a lot of warnings at high warning levels.
  * Fixed errors reported by cppcheck.
  * Fixed Simian warnings in various parts of the Ember+ libraries.
  * Fixed a broken link in the Ember+ documentation.

### Miscellaneous changes ###
  * Declared the step property of the parameter as deprecated.<br />The documentation contains a hint that this property may also be removed in future releases of the libraries.
  * Declared `GlowRootElementCollection::create()` as deprecated.
  * Corrected target prefix for libember and libember\_slim to avoid the double "liblib" prefix on Unix like systems.
  * Modified linker options to set RPATH to '.' on Unix like systems.
  * Added (currently failing) test for [issue #6](https://code.google.com/p/ember-plus/issues/detail?id=#6).


## Ember+ SDK 1.4.0 Release Notes ##

### Overview ###

Version 1.4.0 of the Ember+ SDK is a feature release that introduces provider specified callable functions the GLOW DTD.

Apart from this new feature this release also contains numerous fixes and stability improvements.

### Additions ###

  * Added a method to `glow::Value` to convert it to an instance of `ber::Value`.
  * Added methods `hasEnumeration` and `effectiveParameter` method to `GlowParameterBase`.
  * Added the enumeration entry `ParameterType::None` to indicate that the type is unknown or not present.
  * The methods `minimum`, `maximum`, `value` and `defaultValue` of the class `GlowParameterBase` now return an instance of `Value` or `MinMax` with the parameter type set to `None` when the requested value is not present.
  * Added comparison operators for the `ObjectIdentifier` class.

### Fixes ###

  * Fixed issues #4, #5, #10, #11 and #12.
  * Fixed encoding of real numbers that treated the mantiassa as signed.
  * Fixed encoding of unsigned ling values that caused the encoded value to contain a leading zero.
  * Fixed `DomReader` not decoding values of type `OctetString`.
  * Fixed wrong GLOW tag of `EmberPlus-Glow.MatrixContents.labels`.