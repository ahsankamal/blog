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

#To be continued...