#Intro

**Ruby** is a dynamic, open source and truly object oriented programming language. It has a very clean and elegant syntax that makes it easy for a developer to learn it quickly. It is a scripting language similar to python. Many big websites like *github, basecamp, twitter etc* were built using **Ruby on Rails**, a very famous MVC web application framework.

#Getting started
Open the terminal and type `ruby -v` to check the current version of ruby installed in your system.
```
AhshanKamalmac:blog ahsan.kamal$ ruby -v
ruby 2.3.1p112 (2016-04-26 revision 54768) [x86_64-darwin15]
```

If you don't have ruby installed then first install rvm*(ruby version manager)* and ruby by running following commands.
```
\curl -sSL https://get.rvm.io | bash -s stable
rvm -v
sudo rvm install 2.3.1
rvm list rubies 
rvm use 2.3.1
```
Now type *irb* to invoke interactive ruby shell. IRB is a read–eval–print loop (REPL) for ruby language. It is a very useful tool for testing small chunks of code.

There are no primitive data types in ruby. All the data are represented as object in ruby. Some of the data types supported in ruby are shown below.
```
2.3.1 :001 > 7.class
 => Fixnum 
2.3.1 :001 > 123456789876543212345678987654321.class
 => Bignum  
2.3.1 :002 > 7.0.class
 => Float 
2.3.1 :003 > true.class
 => TrueClass 
2.3.1 :004 > nil.class
 => NilClass 
2.3.1 :005 > "abcd".class
 => String 
2.3.1 :006 > :abcd.class
 => Symbol 
2.3.1 :007 > (1..7).class
 => Range 
2.3.1 :008 > [].class
 => Array 
2.3.1 :009 > {}.class
 => Hash 
```
Parentheses are optional while calling methods in ruby
```
2.3.1 :010 > 7.object_id
 => 15 
2.3.1 :011 > 7.object_id()
 => 15
```

Calling *.methods* on an object would return an array of methods that can be invoked on that object.
```
2.3.1 :012 > 7.methods
 => [:inspect, :size, :succ, :to_s, :to_f, :div, :divmod, :fdiv, :modulo, :abs, :magnitude, :zero?, :odd?, :even?, :to_int, :to_i, :next, :upto, :chr, :ord, :integer?, :floor, :ceil, :round, :eql?, :positive?, :negative?, :nil?,...] 

2.3.1 :013 > [1,2,3].methods
 => [:fill, :assoc, :rassoc, :uniq, :uniq!, :compact, :compact!, :flatten, :to_h, :flatten!, :shuffle!, :shuffle, :include?, :sort, :count,...] 
```

Difference between *puts* and *print* is that puts adds a newline after executing ruby code, and print does not.
```
2.3.1 :014 > 7.times { print "Hi" }
HiHiHiHiHiHiHi => 7 
2.3.1 :015 > 7.times { puts "Hi" }
Hi
Hi
Hi
Hi
Hi
Hi
Hi
 => 7 
```
##Basic mathematical operations
```
2.3.1 :016 > 7+5
 => 12 
2.3.1 :017 > 7-5
 => 2 
2.3.1 :018 > 7*5
 => 35  
2.3.1 :019 > 7/5
 => 1 
2.3.1 :020 > 7/5.0
 => 1.4 
#Exponentiation
2.3.1 :021 > 2**10
 => 1024
#square root 
2.3.1 :030 > 49**(1/2.0)
 => 7.0  
#cube root
2.3.1 :030 > 27**(1/3.0)
 => 3.0  
#Modulus division
2.3.1 :022 > 7%5
 => 2 
2.3.1 :023 > 7.577.ceil
 => 8 
2.3.1 :024 > 7.577.floor
 => 7 
2.3.1 :025 > 7.577.round
 => 8 
2.3.1 :026 > 4.lcm(3)
 => 12 
2.3.1 :027 > 4.gcd(3)
 => 1 
```
Ruby's Math module
```
2.3.1 :028 > Math::E
 => 2.718281828459045 
2.3.1 :029 > Math::PI
 => 3.141592653589793 
2.3.1 :030 > Math.sqrt(49)
 => 7.0 
2.3.1 :031 > Math.log2(1024)
 => 10.0 
2.3.1 :032 > Math.log10(100)
 => 2.0
#Math.log(a,base) 
2.3.1 :033 > Math.log(1024,2)
 => 10.0 
2.3.1 :034 > Math.log(100,10)
 => 2.0 
2.3.1 :035 > Math.sin(Math::PI/2) + Math.cos(Math::PI/2)
 => 1.0 
```
##Comparison operators
```
2.3.1 :036 > 7 == 7
 => true 
2.3.1 :037 > 7 > 7
 => false 
2.3.1 :038 > 7 <= 9
 => true 
```
"==" : compares only the value of operands

.eql? : compares both value and type 

.equal? : compares object_id
```
2.3.1 :039 > "xyz" == "xyz"
 => true 
2.3.1 :040 > "xyz".eql?("xyz")
 => true 
2.3.1 :041 > "xyz".equal?("xyz")
 => false 
2.3.1 :042 > "xyz".object_id
 => 70236825539940 
2.3.1 :043 > "xyz".object_id
 => 70236825509520 
2.3.1 :044 > :xyz.object_id
 => 1148828 
2.3.1 :045 > :xyz.object_id
 => 1148828 
```
Symbols are immutable strings in ruby.
```
2.3.1 :046 > :xyz.equal?(:xyz)
 => true 
```
Ternary Operator
```
2.3.1 :047 > 7>5 ? true : false
 => true 
2.3.1 :048 > (7>5 and (7>4 or 7<4)) ? "y": "n"
 => "y" 
2.3.1 :049 > "ab" == "ab" || !(7>5 && 7<10) ? "y":"n"
 => "y" 
```

##Converting Integer to a number in some other base*(binary, octal, hexadecimal)* and vice versa.

Integer.to_s(base)

String.to_i(base)
```
2.3.1 :050 > 15.to_s(16)
 => "f" 
2.3.1 :051 > 15.to_s(2)
 => "1111"
2.3.1 :052 > 15.to_s(8)
 => "17"
2.3.1 :053 > "110101".to_i(2)
 => 53 
2.3.1 :054 > "ab".to_i(16)
 => 171 
```

##Range operator

".." : inclusive range

"..." : excludes the upper limit
```
2.3.1 :055 > (1..7).to_a
 => [1, 2, 3, 4, 5, 6, 7]
2.3.1 :056 > (1...7).to_a
 => [1, 2, 3, 4, 5, 6] 
```
"a === b" : returns true when b is a member of set defined by a.

"===" : this *case equality operator* is commonly used within a when clause of a case statement.
```
2.3.1 :057 > (1..7) === 3
 => true 
2.3.1 :058 > (1..7) === 8
 => false 
2.3.1 :059 > (1..7) === 7
 => true 
2.3.1 :060 > (1...7) === 7
 => false 
```
##Assignment operators
```
2.3.1 :061 > a=1
 => 1 
2.3.1 :062 > b=2
 => 2 
#"a+=b" means a=a+b 
2.3.1 :063 > a+=b
 => 3 
2.3.1 :064 > a-=b
 => 1 
2.3.1 :065 > a*=b
 => 2 
2.3.1 :066 > a
 => 2 
2.3.1 :067 > b
 => 2 
2.3.1 :068 > a**=b
 => 4 
2.3.1 :069 > a
 => 4 
2.3.1 :070 > b
 => 2 
2.3.1 :071 > a/=b
 => 2 
```
"a||=b" is eqivalent to "a || a = b", (it means if a is false, nil or undefined then assign value of b to a)
```
2.3.1 :072 > a=nil
 => nil 
2.3.1 :073 > b=7
 => 7 
2.3.1 :074 > a||=b
 => 7 
2.3.1 :075 > a||=10
 => 7 
```
Parallel Assignment
```
2.3.1 :076 > a=5
 => 5 
2.3.1 :077 > b=7
 => 7 
2.3.1 :078 > a,b = b,a
 => [7, 5] 
2.3.1 :079 > a
 => 7 
2.3.1 :080 > b
 => 5 
```
##Binary operators
Binary left shift by n bits means multiplying by 2^n
```
2.3.1 :081 > 2<<1
 => 4 
2.3.1 :082 > 2<<4
 => 32 
```
Binary right shift by n bits means dividing by 2^n
```
2.3.1 :083 > 32>>1
 => 16 
```
Binary And(&), OR(|), XOR(^) operations are also supported by ruby.

##String

**String Concatenation**: '+' vs '<<'

'+' operator returns a new string after concatenation, while '<<' concatenates string inplace.
```
2.3.1 :016 > x=3+4
 => 7 
2.3.1 :019 > "3 + 4 is " + x.to_s + "."
 => "3 + 4 is 7."
2.3.1 :093 > a='one'
 => "one" 
2.3.1 :094 > a.object_id
 => 70326373333420 
2.3.1 :095 > a=a+'two'
 => "onetwo" 
2.3.1 :096 > a.object_id
 => 70326364940240 
2.3.1 :097 > a<<'three'
 => "onetwothree" 
2.3.1 :098 > a.object_id
 => 70326364940240 
```

**String interpolation** means evaluating any ruby code present in the double quoted string literal and substituting the code with its result.
It is faster than string concatenation and more commonly used within ruby community.
```
2.3.1 :020 > "3 + 4 is #{3+4}."
 => "3 + 4 is 7." 
```

**Single quoted vs double quoted** string literals.

Double quoted strings are more flexible bcoz they supports string interpolation and many escape sequences.
```
2.3.1 :021 > '3+4 is #{3+4}'
 => "3+4 is \#{3+4}"
2.3.1 :040 > puts 'Learn\truby\nthe easy\tway.'
Learn\truby\nthe easy\tway.
 => nil 
2.3.1 :041 > puts "Learn\truby\nthe easy\tway."
Learn	ruby
the easy	way.
 => nil 
 ```
Use backslash character to escape the special characters from being interpreted by ruby inside double quotes.
```
2.3.1 :044 > puts "Learn \"ruby\" \\nthe easy\\tway."
Learn "ruby" \nthe easy\tway.
 => nil 
2.3.1 :053 > puts "Learn Ruby \
2.3.1 :054"> the \
2.3.1 :055"> easy way."
Learn Ruby the easy way.
 => nil 
```
**String formatting**
```
2.3.1 :056 > puts "%d + %d is %s" %[3,4,'seven']
3 + 4 is seven
 => nil 
2.3.1 :057 > puts "%f + %f is %.2f" % [1.1111,0.1111,1.1111+0.1111]
1.111100 + 0.111100 is 1.22
 => nil 
 
2.3.1 :065 > a=3
 => 3 
2.3.1 :066 > b=4
 => 4 
2.3.1 :067 > puts "%{x} + %{y} is %{z}" % {x: a, y: b, z: a+b} 
3 + 4 is 7
 => nil 
 
2.3.1 :068 > sprintf("%f + %f is %.2f",1.1111,0.1111,1.1111+0.1111)
 => "1.111100 + 0.111100 is 1.22" 
 
2.3.1 :069 > printf("%f + %f is %.2f",1.1111,0.1111,1.1111+0.1111)
1.111100 + 0.111100 is 1.22 => nil 

2.3.1 :085 > %w[one two three]
 => ["one", "two", "three"] 
2.3.1 :086 > %i[one two three]
 => [:one, :two, :three]
```
**String methods**
```
2.3.1 :099 > str = String.new("LearnRubyTheEasyWay")
 => "LearnRubyTheEasyWay" 
 
#str[index], str[start,length], str[range] 
2.3.1 :100 > str[0]
 => "L" 
#negative index means 1-based position from end of the string. 
2.3.1 :101 > str[-1]
 => "y" 
 
#str[start,length] 
2.3.1 :120 > str[1,5]
 => "earnR"
 
#range object can be used to print substring 
2.3.1 :102 > str[0..7]
 => "LearnRub" 
2.3.1 :103 > str[0...7]
 => "LearnRu"
2.3.1 :107 > str[-5..1000]
 => "syWay" 
2.3.1 :111 > str[10000]
 => nil 
 
#str.slice(index), str.slice(start,length), str.slice(range])
2.3.1 :121 > str.slice(1,5)
 => "earnR" 
2.3.1 :122 > str.slice(1..5)
 => "earnR" 
2.3.1 :123 > str.slice(1)
 => "e" 

2.3.1 :118 > str.length
 => 19 
2.3.1 :132 > str.size
 => 19 
2.3.1 :133 > str.bytesize
 => 19  
2.3.1 :119 > str.reverse
 => "yaWysaEehTybuRnraeL" 
2.3.1 :179 > "  ahsan  ".strip
 => "ahsan"

2.3.1 :188 > 'ahsan'.hash
 => 3770592549771597771 
2.3.1 :187 > 'ahsan'.hash == 'ahsan'.hash
 => true 
2.3.1 :189 > :ahsan.hash
 => 3603 

2.3.1 :206 > 'one '*7
 => "one one one one one one one " 

2.3.1 :211 > "The Algorist".downcase
 => "the algorist" 
2.3.1 :212 > "The Algorist".upcase!
 => "THE ALGORIST"

2.3.1 :109 > "one two three".split
 => ["one", "two", "three"] 
2.3.1 :110 > "one,two,three".split(',')
 => ["one", "two", "three"] 
2.3.1 :112 > ["one", "two", "three"].join(",")
 => "one,two,three" 
```
Ruby method containing bang(exclamation mark) at the end will modify the object upon which it is called. 
```
2.3.1 :144 > s="one\n"
 => "one\n" 
2.3.1 :145 > s.chomp
 => "one" 
2.3.1 :146 > s
 => "one\n" 
2.3.1 :147 > s.chomp!
 => "one" 
2.3.1 :148 > s
 => "one" 
```
Ruby method containing ? at the end will return either true or false.
```
2.3.1 :151 > "one two three".include?('two')
 => true 
2.3.1 :152 > "one two three".include?('four')
 => false 
2.3.1 :153 > "".empty?
 => true 
2.3.1 :203 > "one two one".start_with?("one")
 => true 
2.3.1 :204 > "one two one".end_with?("one")
 => true  
```
**sub** method replace only first matched occurence, **gsub** replaces all matched occurences.
```
#string.gsub('match','replacement')
2.3.1 :159 > s = "one two three one"
 => "one two three one" 
2.3.1 :160 > s.sub('one','1')
 => "1 two three one" 
 
2.3.1 :161 > s
 => "one two three one" 
2.3.1 :162 > s.gsub('one','1')
 => "1 two three 1" 
 
2.3.1 :163 > s
 => "one two three one" 
2.3.1 :164 > s['one']='1'
 => "1" 
2.3.1 :165 > s
 => "1 two three one" 
2.3.1 :166 > s['one']='1'
 => "1" 
2.3.1 :167 > s
 => "1 two three 1" 
2.3.1 :168 > s['one']='1'
IndexError: string not matched
	from (irb):168:in `[]='
	from (irb):168
	from /Users/ahsan.kamal/.rvm/rubies/ruby-2.3.1/bin/irb:11:in `<main>'
 ```
Use **index** method to find first occurence of matched substring.
```
2.3.1 :173 > s
 => "1 two three 1" 
2.3.1 :174 > s.index('three')
 => 6 
```
Use **scan** method to find all matching substring.
```
#string.scan(regex)
2.3.1 :177 > "1 one1 two22 3 thre3e f4our".scan(/\d+/)
 => ["1", "1", "22", "3", "3", "4"] 
``` 
Strings are mutable but they can be made immutable by using **freeze** method.
```
2.3.1 :199 > s=''
 => "" 
2.3.1 :200 > s<<'one'
 => "one" 
2.3.1 :201 > s.freeze
 => "one" 
2.3.1 :202 > s<<'two'
RuntimeError: can't modify frozen String
	from (irb):202
	from /Users/ahsan.kamal/.rvm/rubies/ruby-2.3.1/bin/irb:11:in `<main>'
```
**Iterating strings**
```
2.3.1 :208 > '1234567'.each_char {|c| puts c}
1
2
3
4
5
6
7
 => "1234567" 

2.3.1 :209 > '1234567'.each_byte {|c| puts c}
49
50
51
52
53
54
55
 => "1234567" 

2.3.1 :210 > '1234567'.each_line {|c| puts c}
1234567
 => "1234567" 
``` 

#To be continued...
