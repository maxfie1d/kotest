---
id: genslist
title: Generators List
slug: property-test-generators-list.html
sidebar_label: Generators List
---

This page lists all current generators in Kotest. There are two types of generator - [arbitrary](gens.md#arbitrary)
and [exhaustive](gens.md#exhaustive).

Most generators are available on all platforms. Some are JVM or JS specific.

| Generator    | Description | JVM | JS | Native |
| -------- | ----------- | --- | --- | ------ |
| **Numerics** |
| `Arb.int(range)` | Randomly chosen ints in the given range. If the range is not specified then all integers are considered. The edgecases are `Int.MIN_VALUE`, `Int.MAX_VALUE`, 0, 1, -1 | ✓ | ✓ | ✓ |
| `Arb.long(range)` | Randomly chosen longs in the given range. If the range is not specified then all longs are considered. The edgecases are `Long.MIN_VALUE`, `Long.MAX_VALUE`, 0, 1, -1 | ✓ | ✓ | ✓ |
| `Arb.nats(range)` | Randomly chosen natural numbers in the given range. If range is not specified then the default is `Int.MAX_VALUE`. The edgecases are `Int.MAX_VALUE`, 1 | ✓ | ✓ | ✓ |
| `Arb.negativeInts(range)` | Randomly chosen negative integers in the given range. The edgecases are `Int.MIN_VALUE`, -1 | ✓ | ✓ | ✓ |
| `Arb.positiveInts(range)` | Randomly chosen positive integers in the given range. The edgecases are `Int.MAX_VALUE`, 1 | ✓ | ✓ | ✓ |
| `Arb.double(range)` | Randomly chosen doubles in the given range. The edgecases are `Double.MIN_VALUE`, `Double.MAX_VALUE`, `Double.NEGATIVE_INFINITY`, `Double.NaN`, `Double.POSITIVE_INFINITY`, 0.0, 1.0, -1.0, 1e300 | ✓ | ✓ | ✓ |
| `Arb.positiveDoubles(range)` | Randomly chosen positive doubles in the given range. The edgecases are `Double.MIN_VALUE`, `Double.MAX_VALUE`, `Double.POSITIVE_INFINITY`, 1.0, 1e300 | ✓ | ✓ | ✓ |
| `Arb.negativeDoubles(range)` | Randomly chosen negative doubles in the given range. The edgecases are `Double.NEGATIVE_INFINITY`, -1.0 | ✓ | ✓ | ✓ |
| `Exhaustive.int(range)` | Returns all ints in the given range. | ✓ | ✓ | ✓ |
| `Exhaustive.long(range)` | Returns all longs in the given range. | ✓ | ✓ | ✓ |
| `Arb.multiples(k, max)` | Generates multiples of k up a max value. The edgecases are `0`. | ✓ | ✓ | ✓ |
| `Arb.factors(k)` | Generates factors of k. | ✓ | ✓ | ✓ |
| **Nulls** |
| `arb.orNull()` | Generates random values from the arb instance, with null values mixed in. For example, `Arb.int().orNull()` could generate `1, -1, null, 8, 17`, and so on. Has overloaded versions to control the frequency of nulls being generated.| ✓ | ✓ | ✓ |
| `arb.orNull(nullProbability)` | Generates random values from the arb instance, with null values mixed in using the defined probability. | ✓ | ✓ | ✓ |
| **Bytes** |
| `Arb.byte(min, max)` | Generates bytes within the given bounds. The edgecases are `0`, `-1`, `1` `min`, `max`. | ✓ | ✓ | ✓ |
| `Arb.byteArrays(generateArrayLength, max)` | Generates byte arrays with the size of the array taken as random values from the generateArrayLength arb, and the contents of the array provided by the generateContents arb. | ✓ | ✓ | ✓ |
| **Booleans** |
| `Arb.boolean()` | Returns random true and false values. | ✓ | ✓ | ✓ |
| `Exhaustive.boolean()` | Alternatives between true and false. | ✓ | ✓ | ✓ |
| **Chars** |
| `Arb.char(range1, range2,...)` | Returns random char's generated from one or more given ranges. By supporting multiple ranges, it is possible to specific non-consecutive ranges of characters to populate values from. | ✓ | ✓ | ✓ |
| **Enums** |
| `Arb.enum<T>()` | Randomly selects constants from the given enum. | ✓ | ✓ | ✓ |
| `Exhaustive.enum<T>()` | Iterates all the constants defined in the given enum. | ✓ | ✓ | ✓ |
| **Geo** |
| `Arb.latlong()` | Generates random pair's of doubles, where each double is in the range -180 to 180. | ✓ | ✓ | ✓ |
| **Strings** |
| `Arb.string(range)` | Generates random printable strings with a randomly chosen size from the given range. If rangei s not specified then (0..100) is used. The edgecases include empty string, a blank string and a unicode string. | ✓ | ✓ | ✓ |
| `Exhaustive.azstring(range)` | Returns all A-Z strings in the given range. For example if range was 1..2 then a, b, c, ...., yz, zz would be included. | ✓ | ✓ | ✓ |
| `Arb.email(localPartGen, domainGen)` | Generates random emails where the local part and domain part are random strings generated by the given generators. A default value is provided for both. | ✓ | ✓ | ✓ |
| `Arb.emailLocalPart()` | Generates random local email parts | ✓ | ✓ | ✓ |
| `Arb.uuid(type)` | Generates random UUIDs of the given type | ✓ |  |  |
| `Arb.domain(tlds, labelArb)` | Generates random domains with a random tld (defaults to any of the top 120 TLDs) and a label generator, which generates domain parts. | ✓ | ✓ | ✓ |
| **Builders** |
| `Arb.create(fn)` | Generates values using the supplied function. | ✓ | ✓ | ✓ |
| `Arb.bind(arbA, arbB, fn)` | Generates values by pulling a value from each of the two given arbs and then passing those values to the supplied function. | ✓ | ✓ | ✓ |
| `Arb.bind(arbA, arbB, arbC, fn)` | Generates values by pulling a value from each of the three given arbs and then passing those values to the supplied function. | ✓ | ✓ | ✓ |
| `Arb.bind(arbA, ...., fn)` | Generates values by pulling a value from each of the given arbs and then passing those values to the supplied function. | ✓ | ✓ | ✓ |
| **Combinatorics** |
| `Arb.choose(pairs)` | Generates values based on weights. For example, `Arb.choose(1 to 'A', 2 to 'B')` will generate 'A' 33% of the time and 'B' 66% of the time. | ✓ | ✓ | ✓ |
| `Arb.frequency(list)` | Alias to choose | ✓ | ✓ | ✓ |
| `Arb.shuffle(list)` | Generates random permutations of a list. For example, `Arb.shuffle(listOf(1,2,3))` could generate `listOf(3,1,2)`, `listOf(1,3,2)` and so on. | ✓ | ✓ | ✓ |
| `Arb.choice(arbs)` | Randomly selects one of the given arbs and then uses that to generate the next element.  | ✓ | ✓ | ✓ |
| `Arb.subsequence(list)` | Generates a random subsequence of the given list starting at index 0 and including the empty list. For example, `Arb.subsequence(listOf(1,2,3))` could generate `listOf(1)`, `listOf(1,2)`, and so on. | ✓ | ✓ | ✓ |
| **Collections** |
| `Arb.list(gen, range)` | Generates lists where values are generated by the given element generator. The size of each list is determined randomly by the specified range. | ✓ | ✓ | ✓ |
| `Arb.set(gen, range)` | Generates sets where values are generated by the given element generator. The size of each set is determined randomly by the specified range. The slippage argument specifies how many attempts will be made to generate each element before erroring, in the case that the underlying arb does not have enough unique values to satisify the set size. | ✓ | ✓ | ✓ |
| `Arb.set(gen, range, slippage)` | Generates sets where values are generated by the given element generator. The size of each set is determined randomly by the specified range. | ✓ | ✓ | ✓ |
| `Arb.element(collection)` | Randomly selects one of the elements of the given collection. | ✓ | ✓ | ✓ |
| `Arb<T>.chunked(range)` | Generates lists where each list is populated from elements of this receiver. The size of each size is randomly chosen within the given range. | ✓ | ✓ | ✓ |
| `Exhaustive.collection(list)` | Enumerates each element of the list one by one. | ✓ | ✓ | ✓ |
| **Tuples**|
| `Arb.pair(arb1, arb2) | Generates `Pair` instances where each value of the pair is drawn from the two provided arbs | ✓ | ✓ | ✓ |
| `Arb.triple(arb1, arb2, arb3) | Generates `Triple` instances where each value of the triple is drawn from the three provided arbs | ✓ | ✓ | ✓ |
| **Dates** |
| `Arb.date(ranges)` | Generates random dates with the year between the given range |  | ✓ |  |
| `Arb.datetime(ranges)` | Generates random date times with the year between the given range |  | ✓ |  |
| `Arb.localDateTime(ranges)` | Generates random LocalDateTime's with the year between the given range | ✓ |  |  |
| `Arb.localDate(ranges)` | Generates random LocalDate's with the year between the given range | ✓ |  |  |
| **Kotlinx DateTime** | Requires `kotest-property-datetime` module |
| `Arb.date(yearRange)` | Generates `LocalDate`s with the year between the given range and other fields randomly. | ✓ | ✓ | ✓ |
| `Arb.date(yearRange, hourRange, minuteRange, secondRage)` | Generates `LocalDate`s with all fields in the given ranges | ✓ | ✓ | ✓ |
| `Arb.instance(range)` | Generates `Instant`s with the epoch randomly generated in the given range | ✓ | ✓ | ✓ |
