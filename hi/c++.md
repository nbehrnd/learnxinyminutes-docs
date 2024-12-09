---
language: C++
filename: learncpp-hi.cpp
contributors:
    - ["Steven Basart", "https://github.com/xksteven"]
    - ["Matt Kline", "https://github.com/mrkline"]
    - ["Geoff Liu", "http://geoffliu.me"]
    - ["Connor Waters", "https://github.com/connorwaters"]
    - ["Ankush Goyal", "https://github.com/ankushg07"]
    - ["Jatin Dhankhar", "https://github.com/jatindhankhar"]
translators:
    - ["Jishan Shaikh", "https://github.com/jishanshaikh4"]
---

C++ एक सिस्टम प्रोग्रामिंग लैंग्वेज है जो,
[इसके आविष्कारक बजेर्न स्ट्राउस्ट्रप के अनुसार](https://channel9.msdn.com/Events/Lang-NEXT/Lang-NEXT-2014/Keynote),
के लिए डिजाइन किया गया था

* एक "बेहतर सी" बनें
* डेटा एब्स्ट्रैक्शन का समर्थन करें
* ऑब्जेक्ट-ओरिएंटेड प्रोग्रामिंग का समर्थन करें
* सामान्य प्रोग्रामिंग का समर्थन करें

हालांकि इसका सिंटैक्स नई भाषाओं की तुलना में अधिक कठिन या जटिल हो सकता है, इसका व्यापक रूप से उपयोग किया जाता है क्योंकि यह मूल निर्देशों को संकलित करता है जो हो सकते हैं सीधे प्रोसेसर द्वारा चलाया जाता है और हार्डवेयर पर कड़ा नियंत्रण प्रदान करता है (जैसे सी) जेनेरिक, अपवाद और कक्षाओं जैसी उच्च-स्तरीय सुविधाओं की पेशकश करते हुए। गति और कार्यक्षमता का यह संयोजन C++ बनाता है | सबसे व्यापक रूप से उपयोग की जाने वाली प्रोग्रामिंग भाषाओं में से एक।

```c++
//////////////////
// सी . से तुलना
//////////////////

// C++ _लगभग_C का सुपरसेट है और इसके लिए अपना मूल सिंटैक्स साझा करता है
// परिवर्तनीय घोषणाएं, आदिम प्रकार, और कार्य।

// सी की तरह ही, आपके प्रोग्राम का एंट्री पॉइंट एक फंक्शन है, जिसे कहा जाता है
// मुख्य एक पूर्णांक वापसी प्रकार के साथ।
// यह मान प्रोग्राम की निकास स्थिति के रूप में कार्य करता है।
// अधिक जानकारी के लिए https://en.wikipedia.org/wiki/Exit_status देखें।
int main(int argc, char** argv)
{
    // कमांड लाइन तर्क उसी तरह argc और argv द्वारा पारित किए जाते हैं
    // वे सी में हैं।
    // argc तर्कों की संख्या को इंगित करता है,
    // और argv सी-स्टाइल स्ट्रिंग्स (चार *) की एक सरणी है
    // तर्कों का प्रतिनिधित्व करते हैं।
    // पहला तर्क वह नाम है जिसके द्वारा प्रोग्राम को बुलाया गया था।
    // यदि आप तर्कों की परवाह नहीं करते हैं तो argc और argv को छोड़ा जा सकता है,
    // int main का फंक्शन सिग्नेचर देना ()

    // 0 की निकास स्थिति सफलता को इंगित करती है।
    return 0;
}

// हालाँकि, C++ निम्नलिखित में से कुछ तरीकों से भिन्न होता है:

// सी ++ में, वर्ण अक्षर वर्ण हैं
sizeof('c') == sizeof(char) == 1

// सी में, चरित्र अक्षर ints . हैं
sizeof('c') == sizeof(int)


// सी ++ में सख्त प्रोटोटाइप है
void func(); // फ़ंक्शन जो कोई तर्क स्वीकार नहीं करता है

// सी में
void func(); // फ़ंक्शन जो किसी भी संख्या में तर्कों को स्वीकार कर सकता है

// C++ में NULL के बजाय nullptr का प्रयोग करें
int* ip = nullptr;

// सी मानक हेडर सी ++ में उपलब्ध हैं।
// सी हेडर .h में समाप्त होते हैं, जबकि
// सी ++ हेडर "सी" के साथ उपसर्ग कर रहे हैं और कोई ".एच" प्रत्यय नहीं है।

// सी ++ मानक संस्करण:
#include <cstdio>

// सी मानक संस्करण:
#include <stdio.h>

int main()
{
    printf("Hello, world!\n");
    return 0;
}

///////////////////////
// फंक्शन ओवरलोडिंग
///////////////////////

// सी ++ फ़ंक्शन ओवरलोडिंग का समर्थन करता है
// बशर्ते प्रत्येक फ़ंक्शन अलग-अलग पैरामीटर लेता है।

void print(char const* myString)
{
    printf("String %s\n", myString);
}

void print(int myInt)
{
    printf("My int is %d", myInt);
}

int main()
{
    print("Hello"); // Resolves to void print(const char*)
    print(15); // Resolves to void print(int)
}

/////////////////////////////
// डिफ़ॉल्ट फ़ंक्शन तर्क
/////////////////////////////

// आप किसी फ़ंक्शन के लिए डिफ़ॉल्ट तर्क प्रदान कर सकते हैं
// अगर वे कॉलर द्वारा प्रदान नहीं किए जाते हैं।

void doSomethingWithInts(int a = 1, int b = 4)
{
    // यहां इनट्स के साथ कुछ करें
}

int main()
{
    doSomethingWithInts();      // a = 1,  b = 4
    doSomethingWithInts(20);    // a = 20, b = 4
    doSomethingWithInts(20, 5); // a = 20, b = 5
}

// डिफ़ॉल्ट तर्क तर्क सूची के अंत में होना चाहिए।

void invalidDeclaration(int a = 1, int b) // Error!
{
}


/////////////
// नेमस्पेस
/////////////

// नेमस्पेस वैरिएबल, फंक्शन के लिए अलग-अलग स्कोप प्रदान करते हैं,
// और अन्य घोषणाएं।
// नेमस्पेस को नेस्ट किया जा सकता है।

namespace First {
    namespace Nested {
        void foo()
        {
            printf("This is First::Nested::foo\n");
        }
    } // अंत नामस्थान नेस्टेड
} // अंतिम नाम स्थान पहले

namespace Second {
    void foo()
    {
        printf("This is Second::foo\n");
    }
}

void foo()
{
    printf("This is global foo\n");
}

int main()
{
    // नेमस्पेस सेकेंड से वर्तमान दायरे में सभी प्रतीकों को शामिल करता है। ध्यान दें
    // वह बस foo() अब काम नहीं करता है, क्योंकि यह अब अस्पष्ट है कि क्या
    // हम फू को नेमस्पेस सेकेंड या टॉप लेवल में कॉल कर रहे हैं।
    using namespace Second;

    Second::foo(); // प्रिंट "यह दूसरा है :: फू"
    First::Nested::foo(); // प्रिंट "यह पहला है :: नेस्टेड :: फू"
    ::foo(); // प्रिंट करता है "यह वैश्विक फू है"
}

///////////////
// इनपुट आउटपुट
///////////////

// सी ++ इनपुट और आउटपुट स्ट्रीम का उपयोग करता है
// cin, cout, और cerr stdin, stdout और stderr का प्रतिनिधित्व करते हैं।
// << इंसर्शन ऑपरेटर है और >> एक्सट्रैक्शन ऑपरेटर है।

#include <iostream> // I/O स्ट्रीम के लिए शामिल करें

using namespace std; // स्ट्रीम एसटीडी नेमस्पेस (मानक पुस्तकालय) में हैं

int main()
{
   int myInt;

   // स्टडआउट (या टर्मिनल / स्क्रीन) पर प्रिंट करता है
   cout << "Enter your favorite number:\n";
   // इनपुट लेता है
   cin >> myInt;

   // cout को भी स्वरूपित किया जा सकता है
   cout << "Your favorite number is " << myInt << '\n';
   // प्रिंट करता है "आपका पसंदीदा नंबर <myInt>" है

   cerr << "Used for error messages";
}

//////////
// स्ट्रिंग्स
//////////

// सी ++ में स्ट्रिंग्स ऑब्जेक्ट हैं और इसमें कई सदस्य कार्य हैं
#include <string>

using namespace std; // स्ट्रिंग्स नेमस्पेस एसटीडी (मानक पुस्तकालय) में भी हैं

string myString = "Hello";
string myOtherString = " World";

// + का उपयोग संयोजन के लिए किया जाता है।
cout << myString + myOtherString; // "Hello World"

cout << myString + " You"; // "Hello You"

// सी ++ स्ट्रिंग्स म्यूटेबल हैं।
myString.append(" Dog");
cout << myString; // "Hello Dog"


/////////////
// संदर्भ
/////////////

// सी में वाले जैसे पॉइंटर्स के अलावा,
// सी ++ में _references_ हैं।
// ये पॉइंटर प्रकार हैं जिन्हें एक बार सेट करने के बाद पुन: असाइन नहीं किया जा सकता है
// और शून्य नहीं हो सकता।
// उनके पास वैरिएबल के समान सिंटैक्स भी है:
// नहीं * dereferencing के लिए आवश्यक है और
// और (का पता) असाइनमेंट के लिए उपयोग नहीं किया जाता है।

using namespace std;

string foo = "I am foo";
string bar = "I am bar";


string& fooRef = foo; // यह foo का संदर्भ बनाता है।
fooRef += ". Hi!"; // संदर्भ के माध्यम से फू को संशोधित करें
cout << fooRef; // प्रिंट "I am foo. Hi!"

// "fooRef" को पुन: असाइन नहीं करता है। यह "फू = बार" जैसा ही है, और
// फू == "मैं बार हूँ"
// इस लाइन के बाद।
cout << &fooRef << endl;  // फू का पता प्रिंट करता है
fooRef = bar;
cout << &fooRef << endl; // अभी भी फू का पता प्रिंट करता है
cout << fooRef;  // प्रिंट "I am bar"

// fooRef का पता वही रहता है, यानी यह अभी भी foo की बात कर रहा है।


const string& barRef = bar; // बार के लिए एक कॉन्स्टेबल संदर्भ बनाएं।
// सी की तरह, कॉन्स्ट वैल्यू (और पॉइंटर्स और रेफरेंस) को संशोधित नहीं किया जा सकता है।
barRef += ". Hi!"; // त्रुटि, कॉन्स्ट संदर्भों को संशोधित नहीं किया जा सकता है।

// साइडट्रैक: इससे पहले कि हम संदर्भों के बारे में अधिक बात करें, हमें एक अवधारणा पेश करनी चाहिए
// एक अस्थायी वस्तु कहा जाता है। मान लीजिए हमारे पास निम्नलिखित कोड है:
string tempObjectFun() { ... }
string retVal = tempObjectFun();

// दूसरी पंक्ति में वास्तव में क्या होता है:
// - एक स्ट्रिंग ऑब्जेक्ट tempObjectFun से लौटाया जाता है
// - तर्क के रूप में लौटाई गई वस्तु के साथ एक नई स्ट्रिंग का निर्माण किया जाता है
// कंस्ट्रक्टर
// - लौटाई गई वस्तु नष्ट हो जाती है
// लौटाई गई वस्तु को अस्थायी वस्तु कहा जाता है। अस्थायी वस्तुएं हैं
// जब भी कोई फ़ंक्शन किसी ऑब्जेक्ट को लौटाता है, तब बनाया जाता है, और वे नष्ट हो जाते हैं
// संलग्न अभिव्यक्ति के मूल्यांकन का अंत (ठीक है, यह वही है
// मानक कहता है, लेकिन संकलक को इस व्यवहार को बदलने की अनुमति है। ऊपर देखो
// "वापसी मूल्य अनुकूलन" यदि आप इस तरह के विवरण में हैं)। तो इसमें
// कोड:
foo(bar(tempObjectFun()))

// यह मानते हुए कि फू और बार मौजूद हैं, tempObjectFun से लौटाई गई वस्तु है
// बार को पास किया गया, और फू को कॉल करने से पहले इसे नष्ट कर दिया गया।

// अब वापस संदर्भों पर। "संलग्नक के अंत में" का अपवाद
// अभिव्यक्ति" नियम यह है कि यदि एक अस्थायी वस्तु एक कॉन्स्ट संदर्भ के लिए बाध्य है, तो
// किस मामले में इसका जीवन वर्तमान दायरे तक बढ़ जाता है:

void constReferenceTempObjectFun() {
    // constRef अस्थायी वस्तु प्राप्त करता है, और यह इस के अंत तक मान्य है
    // समारोह।
    const string& constRef = tempObjectFun();
    ...
}

// सी ++ 11 में पेश किया गया एक अन्य प्रकार का संदर्भ विशेष रूप से अस्थायी के लिए है
// ऑब्जेक्ट्स। आपके पास इसके प्रकार का एक चर नहीं हो सकता है, लेकिन इसमें पूर्वता होती है
// अधिभार संकल्प:

void someFun(string& s) { ... }  // नियमित संदर्भ
void someFun(string&& s) { ... }  // अस्थायी वस्तु का संदर्भ

string foo;
someFun(foo);  // नियमित संदर्भ के साथ संस्करण को कॉल करें
someFun(tempObjectFun());  // अस्थायी संदर्भ के साथ संस्करण को कॉल करें

// उदाहरण के लिए, आप कंस्ट्रक्टर के इन दो संस्करणों को देखेंगे
// std::basic_string:
basic_string(const basic_string& other);
basic_string(basic_string&& other);

// विचार यह है कि अगर हम एक अस्थायी वस्तु से एक नई स्ट्रिंग का निर्माण कर रहे हैं (जो
// वैसे भी जल्द ही नष्ट होने जा रहा है), हम अधिक कुशल हो सकते हैं
// कंस्ट्रक्टर जो उस अस्थायी स्ट्रिंग के कुछ हिस्सों को "बचाता" है। आप इसे देखेंगे
// अवधारणा को "मूव सेमेन्टिक्स" के रूप में जाना जाता है।

/////////////////////
// Enums
/////////////////////

// Enums सबसे अधिक उपयोग किए जाने वाले स्थिरांक को मान निर्दिष्ट करने का एक तरीका है
// आसान विज़ुअलाइज़ेशन और कोड को पढ़ना
enum ECarTypes
{
  Sedan,
  Hatchback,
  SUV,
  Wagon
};

ECarTypes GetPreferredCarType()
{
    return ECarTypes::Hatchback;
}

// सी ++ 11 के रूप में एनम को एक प्रकार असाइन करने का एक आसान तरीका है जो हो सकता है
// डेटा के क्रमांकन में उपयोगी और एनम को आगे-पीछे परिवर्तित करना
// वांछित प्रकार और उनके संबंधित स्थिरांक
enum ECarTypes : uint8_t
{
    Sedan, // 0
    Hatchback, // 1
    SUV = 254, // 254
    Hybrid // 255
};

void WriteByteToFile(uint8_t InputValue)
{
    // किसी फ़ाइल में इनपुटवैल्यू को क्रमबद्ध करें
}

void WritePreferredCarTypeToFile(ECarTypes InputCarType)
{
    // एनम को इसके घोषित एनम प्रकार के कारण uint8_t में परिवर्तित कर दिया गया है
    WriteByteToFile(InputCarType);
}

// दूसरी ओर, हो सकता है कि आप नहीं चाहते कि गलती से एनम को एक पूर्णांक में डाला जाए
// टाइप करें या अन्य एनम के लिए ताकि इसके बजाय एक एनम क्लास बनाना संभव हो जो
// परोक्ष रूप से परिवर्तित नहीं किया जाएगा
enum class ECarTypes : uint8_t
{
    Sedan, // 0
    Hatchback, // 1
    SUV = 254, // 254
    Hybrid // 255
};

void WriteByteToFile(uint8_t InputValue)
{
    // किसी फ़ाइल में इनपुटवैल्यू को क्रमबद्ध करें
}

void WritePreferredCarTypeToFile(ECarTypes InputCarType)
{
    // संकलित नहीं होगा, भले ही ECarTypes एक uint8_t एनम के कारण है
    // "एनम क्लास" के रूप में घोषित किया जा रहा है!
    WriteByteToFile(InputCarType);
}

//////////////////////////////////////////
// कक्षाएं और वस्तु-उन्मुख प्रोग्रामिंग
//////////////////////////////////////////

// कक्षाओं का पहला उदाहरण
#include <iostream>

// एक वर्ग घोषित करें।
// कक्षाएं आमतौर पर हेडर (.h या .hpp) फाइलों में घोषित की जाती हैं।
class Dog {
        // सदस्य चर और कार्य डिफ़ॉल्ट रूप से निजी हैं।
    std::string name;
    int weight;

// इसका अनुसरण करने वाले सभी सदस्य सार्वजनिक हैं
// जब तक "निजी:" या "संरक्षित:" नहीं मिलता है।
public:

    // Default constructor
    Dog();

    // सदस्य फ़ंक्शन घोषणाएं (कार्यान्वयन का पालन करें)
    // ध्यान दें कि हम यहां रखने के बजाय std::string का उपयोग करते हैं
    // नेमस्पेस एसटीडी का उपयोग करना;
    // ऊपर।
    // हेडर में कभी भी "नेमस्पेस का उपयोग करके" स्टेटमेंट न डालें।
    void setName(const std::string& dogsName);

    void setWeight(int dogsWeight);

    // ऐसे कार्य जो वस्तु की स्थिति को संशोधित नहीं करते हैं
    // को कॉन्स्ट के रूप में चिह्नित किया जाना चाहिए।
    // यह आपको ऑब्जेक्ट के संदर्भ में दिए जाने पर उन्हें कॉल करने की अनुमति देता है।
    // यह भी ध्यान दें कि कार्यों को स्पष्ट रूप से _virtual_ के रूप में घोषित किया जाना चाहिए
    // व्युत्पन्न कक्षाओं में ओवरराइड करने के लिए।
    // कार्य प्रदर्शन कारणों से डिफ़ॉल्ट रूप से आभासी नहीं हैं।
    virtual void print() const;

    // फंक्शन को क्लास बॉडी के अंदर भी परिभाषित किया जा सकता है।
    // इस तरह परिभाषित कार्य स्वचालित रूप से रेखांकित होते हैं।
    void bark() const { std::cout << name << " barks!\n"; }

    // कंस्ट्रक्टर्स के साथ, C++ डिस्ट्रक्टर्स प्रदान करता है।
    // इन्हें तब कहा जाता है जब कोई वस्तु हटा दी जाती है या दायरे से बाहर हो जाती है।
    // यह RAII जैसे शक्तिशाली प्रतिमानों को सक्षम बनाता है
    // (निचे देखो)
    // विध्वंसक आभासी होना चाहिए यदि एक वर्ग से प्राप्त किया जाना है;
    // यदि यह आभासी नहीं है, तो व्युत्पन्न वर्ग 'विनाशक होगा'
    // यदि ऑब्जेक्ट बेस-क्लास संदर्भ के माध्यम से नष्ट हो जाता है तो कॉल नहीं किया जाएगा
    // या सूचक।
    virtual ~Dog();

}; // अर्धविराम को वर्ग परिभाषा का पालन करना चाहिए।

// क्लास सदस्य फ़ंक्शन आमतौर पर .cpp फ़ाइलों में कार्यान्वित किए जाते हैं।
Dog::Dog()
{
    std::cout << "A dog has been constructed\n";
}

// वस्तुओं (जैसे तार) को संदर्भ द्वारा पारित किया जाना चाहिए
// यदि आप उन्हें संशोधित कर रहे हैं या यदि आप नहीं हैं तो संदर्भ संदर्भ।
void Dog::setName(const std::string& dogsName)
{
    name = dogsName;
}

void Dog::setWeight(int dogsWeight)
{
    weight = dogsWeight;
}

// ध्यान दें कि "आभासी" केवल घोषणा में आवश्यक है, परिभाषा नहीं।
void Dog::print() const
{
    std::cout << "Dog is " << name << " and weighs " << weight << "kg\n";
}

Dog::~Dog()
{
    std::cout << "Goodbye " << name << '\n';
}

int main() {
    Dog myDog; // prints "A dog has been constructed"
    myDog.setName("Barkley");
    myDog.setWeight(10);
    myDog.print(); // prints "Dog is Barkley and weighs 10 kg"
    return 0;
} // prints "Goodbye Barkley"

// विरासत:

// इस वर्ग को सब कुछ विरासत में मिला है और डॉग क्लास से संरक्षित है
// साथ ही निजी लेकिन सीधे निजी सदस्यों / विधियों तक नहीं पहुंच सकता है
// ऐसा करने के लिए सार्वजनिक या संरक्षित विधि के बिना
class OwnedDog : public Dog {

public:
    void setOwner(const std::string& dogsOwner);

    // सभी स्वामित्व वाले कुत्तों के लिए प्रिंट फ़ंक्शन के व्यवहार को ओवरराइड करें। ले देख
    // https://en.wikipedia.org/wiki/Polymorphism_(computer_science)#Subtyping
    // अधिक सामान्य परिचय के लिए यदि आप अपरिचित हैं
    // उपप्रकार बहुरूपता।
    // ओवरराइड कीवर्ड वैकल्पिक है लेकिन सुनिश्चित करता है कि आप वास्तव में हैं
    // बेस क्लास में विधि को ओवरराइड करना।

private:
    std::string owner;
};

// इस बीच, संबंधित .cpp फ़ाइल में:

void OwnedDog::setOwner(const std::string& dogsOwner)
{
    owner = dogsOwner;
}

void OwnedDog::print() const
{
    Dog::print(); // बेस डॉग क्लास में प्रिंट फ़ंक्शन को कॉल करें class
    std::cout << "Dog is owned by " << owner << '\n';
    // प्रिंट करता है "कुत्ता <नाम> है और वजन <वजन>" है
    // "कुत्ता <मालिक> के स्वामित्व में है"
}

//////////////////////////////////////////
// आरंभीकरण और ऑपरेटर ओवरलोडिंग
//////////////////////////////////////////

// सी ++ में आप ऑपरेटरों के व्यवहार को ओवरलोड कर सकते हैं जैसे +, -, *, /, आदि।
// यह एक फ़ंक्शन को परिभाषित करके किया जाता है जिसे कहा जाता है
// जब भी ऑपरेटर का उपयोग किया जाता है।

#include <iostream>
using namespace std;

class Point {
public:
        // सदस्य चर को इस तरह से डिफ़ॉल्ट मान दिया जा सकता है।
    double x = 0;
    double y = 0;

        // एक डिफ़ॉल्ट कंस्ट्रक्टर को परिभाषित करें जो कुछ भी नहीं करता है
    // लेकिन बिंदु को डिफ़ॉल्ट मान (0, 0) पर प्रारंभ करें
    Point() { };

    // The following syntax is known as an initialization list
    // and is the proper way to initialize class member values
    Point (double a, double b) :
        x(a),
        y(b)
    { /* मानों को इनिशियलाइज़ करने के अलावा कुछ न करें */ }

    // + ऑपरेटर को ओवरलोड करें।
    Point operator+(const Point& rhs) const;

    // + = ऑपरेटर को अधिभारित करें
    Point& operator+=(const Point& rhs);

    // - और - = ऑपरेटरों को जोड़ना भी समझ में आता है,
    // लेकिन हम उन्हें संक्षिप्तता के लिए छोड़ देंगे।
};

Point Point::operator+(const Point& rhs) const
{
    // एक नया बिंदु बनाएं जो इस एक और rhs का योग हो।.
    return Point(x + rhs.x, y + rhs.y);
}

// के सबसे बाएं चर के संदर्भ को वापस करने के लिए यह अच्छा अभ्यास है
// सौंपा गया कार्य। `(a += b) == c` इस तरह से काम करेगा।
Point& Point::operator+=(const Point& rhs)
{
    x += rhs.x;
    y += rhs.y;

    // `this` उस वस्तु का सूचक है, जिस पर एक विधि कहलाती है।
    return *this;
}

int main () {
    Point up (0,1);
    Point right (1,0);
    // यह प्वाइंट + ऑपरेटर को कॉल करता है
    // पॉइंट अप + (फ़ंक्शन) को इसके पैरामीटर के रूप में दाईं ओर कॉल करता है
    Point result = up + right;
    // Prints "Result is upright (1,1)"
    cout << "Result is upright (" << result.x << ',' << result.y << ")\n";
    return 0;
}

/////////////////////
// टेम्पलेट्स
/////////////////////

// C++ में टेम्प्लेट ज्यादातर सामान्य प्रोग्रामिंग के लिए उपयोग किए जाते हैं, हालांकि वे हैं
// अन्य भाषाओं में सामान्य निर्माणों की तुलना में बहुत अधिक शक्तिशाली। वे भी
// स्पष्ट और आंशिक विशेषज्ञता और कार्यात्मक-शैली प्रकार का समर्थन करें
// कक्षाएं; वास्तव में, वे एक ट्यूरिंग-पूर्ण कार्यात्मक भाषा एम्बेडेड हैं
// सी ++ में!

// हम उस तरह की सामान्य प्रोग्रामिंग से शुरू करते हैं जिससे आप परिचित हो सकते हैं। सेवा
// एक वर्ग या फ़ंक्शन को परिभाषित करें जो एक प्रकार का पैरामीटर लेता है:
template<class T>
class Box {
public:
    // इस वर्ग में, टी का उपयोग किसी अन्य प्रकार के रूप में किया जा सकता है।
    void insert(const T&) { ... }
};

// संकलन के दौरान, कंपाइलर वास्तव में प्रत्येक टेम्पलेट की प्रतियां बनाता है
// प्रतिस्थापित मापदंडों के साथ, इसलिए वर्ग की पूरी परिभाषा होनी चाहिए
// प्रत्येक आह्वान पर उपस्थित। यही कारण है कि आप टेम्पलेट वर्ग परिभाषित देखेंगे
// पूरी तरह से हेडर फाइलों में।

// स्टैक पर टेम्प्लेट क्लास को इंस्टेंट करने के लिए:
Box<int> intBox;

// और आप इसका उपयोग कर सकते हैं जैसा कि आप उम्मीद करेंगे:
intBox.insert(123);

// आप निश्चित रूप से, नेस्ट टेम्प्लेट कर सकते हैं:
Box<Box<int> > boxOfBox;
boxOfBox.insert(intBox);

// C++11 तक, आपको दो '>' के बीच एक जगह रखनी थी, अन्यथा '>>'
// सही शिफ्ट ऑपरेटर के रूप में पार्स किया जाएगा।

// आप कभी-कभी देखेंगे
// टेम्पलेट<टाइपनाम टी>
// बजाय। 'वर्ग' कीवर्ड और 'टाइपनाम' कीवर्ड _अधिकतर_ हैं
// इस मामले में विनिमेय। पूरी व्याख्या के लिए देखें
// https://en.wikipedia.org/wiki/Typename
// (हाँ, उस कीवर्ड का अपना विकिपीडिया पेज है)।

// इसी तरह, एक टेम्पलेट फ़ंक्शन:
template<class T>
void barkThreeTimes(const T& input)
{
    input.bark();
    input.bark();
    input.bark();
}

// ध्यान दें कि यहां प्रकार के मापदंडों के बारे में कुछ भी निर्दिष्ट नहीं है। संकलक
// उत्पन्न करेगा और फिर टेम्पलेट के प्रत्येक आमंत्रण को टाइप-चेक करेगा, इसलिए
// उपरोक्त फ़ंक्शन किसी भी प्रकार 'T' के साथ काम करता है जिसमें एक कॉन्स 'bark' विधि होती है!

Dog fluffy;
fluffy.setName("Fluffy")
barkThreeTimes(fluffy); // Prints "Fluffy barks" three times.

// टेम्प्लेट मापदंडों का वर्ग होना जरूरी नहीं है:
template<int Y>
void printMessage() {
  cout << "Learn C++ in " << Y << " minutes!" << endl;
}

// और आप स्पष्ट रूप से अधिक कुशल कोड के लिए टेम्पलेट्स को विशेषज्ञ बना सकते हैं। का
// बेशक, विशेषज्ञता के अधिकांश वास्तविक दुनिया के उपयोग इस तरह के रूप में तुच्छ नहीं हैं।
// ध्यान दें कि आपको अभी भी फ़ंक्शन (या वर्ग) को टेम्पलेट के रूप में घोषित करने की आवश्यकता है
// भले ही आपने सभी मापदंडों को स्पष्ट रूप से निर्दिष्ट किया हो।
template<>
void printMessage<10>() {
  cout << "Learn C++ faster in only 10 minutes!" << endl;
}

printMessage<20>();  // Prints "Learn C++ in 20 minutes!"
printMessage<10>();  // Prints "Learn C++ faster in only 10 minutes!"


/////////////////////
// संचालन अपवाद
/////////////////////

// मानक पुस्तकालय कुछ अपवाद प्रकार प्रदान करता है
// (देखें https://en.cppreference.com/w/cpp/error/exception)
// लेकिन किसी भी प्रकार को अपवाद के रूप में फेंका जा सकता है
#include <exception>
#include <stdexcept>

// _try_ ब्लॉक के अंदर फेंके गए सभी अपवादों को बाद में पकड़ा जा सकता है
// _कैच_ हैंडलर।
try {
    // _new_ का उपयोग करके ढेर पर अपवाद आवंटित न करें।
    throw std::runtime_error("A problem occurred");
}

// कॉन्स्ट संदर्भ द्वारा अपवादों को पकड़ें यदि वे ऑब्जेक्ट हैं
catch (const std::exception& ex)
{
    std::cout << ex.what();
}

// पिछले _catch_ ब्लॉक द्वारा नहीं पकड़े गए किसी भी अपवाद को पकड़ता है
catch (...)
{
    std::cout << "Unknown exception caught";
    throw; // Re-throws the exception
}

///////
// आरएआईआई
///////

// RAII का अर्थ  "संसाधन अधिग्रहण आरंभीकरण है"।
// इसे अक्सर C++ में सबसे शक्तिशाली प्रतिमान माना जाता है
// और सरल अवधारणा है कि एक वस्तु के लिए एक निर्माता
// उस वस्तु के संसाधनों को प्राप्त करता है और विनाशक उन्हें जारी करता है।

// यह समझने के लिए कि यह कैसे उपयोगी है,
// एक फ़ंक्शन पर विचार करें जो C फ़ाइल हैंडल का उपयोग करता है:
void doSomethingWithAFile(const char* filename)
{
    // शुरू करने के लिए, मान लें कि कुछ भी विफल नहीं हो सकता है।

    FILE* fh = fopen(filename, "r"); // Open the file in read mode.

    doSomethingWithTheFile(fh);
    doSomethingElseWithIt(fh);

    fclose(fh); // Close the file handle.
}

// दुर्भाग्य से, त्रुटि प्रबंधन से चीजें जल्दी जटिल हो जाती हैं।
// मान लीजिए कि fopen विफल हो सकता है, और वह doSomethingWithTheFile और
// doSomethingElseWithIt विफल होने पर त्रुटि कोड लौटाता है।
// (अपवाद विफलता से निपटने का पसंदीदा तरीका है,
// लेकिन कुछ प्रोग्रामर, विशेष रूप से C बैकग्राउंड वाले,
// अपवादों की उपयोगिता पर असहमत)।
// अब हमें विफलता के लिए प्रत्येक कॉल की जांच करनी होगी और फ़ाइल हैंडल को बंद करना होगा
// यदि कोई समस्या हुई।
bool doSomethingWithAFile(const char* filename)
{
    FILE* fh = fopen(filename, "r"); // फ़ाइल को रीड मोड में खोलें
    if (fh == nullptr) // लौटाया गया सूचक विफलता पर शून्य है।
        return false; // Report that failure to the caller.

    // मान लें कि प्रत्येक फ़ंक्शन विफल होने पर गलत लौटाता है
    if (!doSomethingWithTheFile(fh)) {
        fclose(fh); // फ़ाइल हैंडल को बंद करें ताकि यह लीक न हो।
        return false; // त्रुटि का प्रचार करें।
    }
    if (!doSomethingElseWithIt(fh)) {
        fclose(fh); // फ़ाइल हैंडल को बंद करें ताकि यह लीक न हो।
        return false; // त्रुटि का प्रचार करें।
    }

    fclose(fh); // फ़ाइल हैंडल को बंद करें ताकि यह लीक न हो।
    return true; // सफलता का संकेत दें
}

// सी प्रोग्रामर अक्सर गोटो का उपयोग करके इसे थोड़ा साफ करते हैं:
bool doSomethingWithAFile(const char* filename)
{
    FILE* fh = fopen(filename, "r");
    if (fh == nullptr)
        return false;

    if (!doSomethingWithTheFile(fh))
        goto failure;

    if (!doSomethingElseWithIt(fh))
        goto failure;

    fclose(fh); // Close the file
    return true; // Indicate success

failure:
    fclose(fh);
    return false; // Propagate the error
}

// यदि फ़ंक्शन अपवादों का उपयोग करके त्रुटियों को इंगित करता है,
// चीजें थोड़ी साफ हैं, लेकिन फिर भी उप-इष्टतम हैं।
void doSomethingWithAFile(const char* filename)
{
    FILE* fh = fopen(filename, "r"); // Open the file in shared_ptrread mode
    if (fh == nullptr)
        throw std::runtime_error("Could not open the file.");

    try {
        doSomethingWithTheFile(fh);
        doSomethingElseWithIt(fh);
    }
    catch (...) {
        fclose(fh); // Be sure to close the file if an error occurs.
        throw; // Then re-throw the exception.
    }

    fclose(fh); // Close the file
    // Everything succeeded
}

// इसकी तुलना C++ के फाइल स्ट्रीम क्लास (fstream) के उपयोग से करें
// fstream फ़ाइल को बंद करने के लिए अपने विनाशक का उपयोग करता है।
// ऊपर से याद करें कि विध्वंसक स्वचालित रूप से कहलाते हैं
// जब भी कोई वस्तु दायरे से बाहर हो जाती है।
void doSomethingWithAFile(const std::string& filename)
{
    // ifstream इनपुट फ़ाइल स्ट्रीम के लिए छोटा है
    std::ifstream fh(filename); // Open the file

    // Do things with the file
    doSomethingWithTheFile(fh);
    doSomethingElseWithIt(fh);

} //फ़ाइल स्वचालित रूप से यहाँ विध्वंसक द्वारा बंद कर दी गई है

// इसके _massive_ फायदे हैं:
// 1. चाहे कुछ भी हो जाए,
// संसाधन (इस मामले में फ़ाइल हैंडल) को साफ किया जाएगा।
// एक बार जब आप विध्वंसक को सही ढंग से लिख लेते हैं,
// हैंडल को बंद करना और रिसोर्स को लीक करना भूल जाना _असंभव_ है।
// 2. ध्यान दें कि कोड ज्यादा साफ है।
// विनाशक पर्दे के पीछे फ़ाइल को बंद करने का प्रबंधन करता है
// आपको इसके बारे में चिंता किए बिना।
// 3. कोड अपवाद सुरक्षित है।
// फंक्शन और क्लीनअप में कहीं भी एक अपवाद फेंका जा सकता है
// अभी भी होगा।

// सभी मुहावरेदार सी ++ कोड सभी संसाधनों के लिए बड़े पैमाने पर आरएआईआई का उपयोग करता है।
// अतिरिक्त उदाहरणों में शामिल हैं
// - unique_ptr और shared_ptr . का उपयोग करके मेमोरी
// - कंटेनर - मानक पुस्तकालय लिंक्ड सूची,
// वेक्टर (यानी स्व-आकार देने वाला सरणी), हैश मैप, और इसी तरह
// जब वे दायरे से बाहर हो जाते हैं तो सभी स्वचालित रूप से अपनी सामग्री को नष्ट कर देते हैं।
// - लॉक_गार्ड और यूनिक_लॉक का उपयोग करने वाले म्यूटेक्स


/////////////////////
// स्मार्ट पॉइंटर
/////////////////////

// आम तौर पर एक स्मार्ट पॉइंटर एक ऐसा वर्ग होता है जो "रॉ पॉइंटर" ("नया" का उपयोग) को लपेटता है
// क्रमशः सी में मॉलोक / कॉलोक)। लक्ष्य सक्षम होना है
// स्पष्ट रूप से हटाने की आवश्यकता के बिना इंगित की जा रही वस्तु के जीवनकाल का प्रबंधन करें
// वस्तु। यह शब्द केवल पॉइंटर्स के एक सेट का वर्णन करता है जिसमें
// अमूर्त का उल्लेख किया।
// स्मार्ट पॉइंटर्स को रोकने के लिए कच्चे पॉइंटर्स पर प्राथमिकता दी जानी चाहिए
// जोखिम भरा मेमोरी लीक, जो तब होता है जब आप किसी ऑब्जेक्ट को हटाना भूल जाते हैं।

// कच्चे सूचक का उपयोग:
Dog* ptr = new Dog();
ptr->bark();
delete ptr;

// स्मार्ट पॉइंटर का उपयोग करके, आपको हटाने के बारे में चिंता करने की ज़रूरत नहीं है
// अब वस्तु का।
// एक स्मार्ट पॉइंटर एक नीति का वर्णन करता है, जिसमें संदर्भों की गणना की जाती है
// सूचक। वस्तु नष्ट हो जाती है जब अंतिम
// वस्तु का संदर्भ नष्ट हो जाता है।

// "std::shared_ptr" का उपयोग:
void foo()
{
    // It's no longer necessary to delete the Dog.
    std::shared_ptr<Dog> doggo(new Dog());
    doggo->bark();
}

// संभावित परिपत्र संदर्भों से सावधान रहें !!!
// हमेशा एक संदर्भ होगा, इसलिए इसे कभी नष्ट नहीं किया जाएगा!
std::shared_ptr<Dog> doggo_one(new Dog());
std::shared_ptr<Dog> doggo_two(new Dog());
doggo_one = doggo_two; // p1 references p2
doggo_two = doggo_one; // p2 references p1

// कई प्रकार के स्मार्ट पॉइंटर्स हैं।
// उनका उपयोग करने का तरीका हमेशा एक जैसा होता है।
// यह हमें इस प्रश्न की ओर ले जाता है: हमें प्रत्येक प्रकार के स्मार्ट पॉइंटर का उपयोग कब करना चाहिए?
// std::unique_ptr - इसका उपयोग तब करें जब आप केवल एक संदर्भ रखना चाहते हैं
// वस्तु।
// std::shared_ptr - इसका उपयोग तब करें जब आप इसके लिए कई संदर्भ रखना चाहते हैं
// एक ही वस्तु और यह सुनिश्चित करना चाहते हैं कि इसे हटा दिया गया है
// जब सभी संदर्भ चले गए हैं।
// std::weak_ptr - जब आप एक्सेस करना चाहते हैं तो इसका इस्तेमाल करें
// एक std::shared_ptr की अंतर्निहित वस्तु उस वस्तु को आवंटित किए बिना।
// कमजोर पॉइंटर्स का उपयोग सर्कुलर रेफरेंसिंग को रोकने के लिए किया जाता है।


/////////////////////
// कंटेनर
/////////////////////

// कंटेनर या मानक टेम्पलेट लाइब्रेरी कुछ पूर्वनिर्धारित टेम्पलेट हैं।
// वे इसके तत्वों के लिए भंडारण स्थान का प्रबंधन करते हैं और प्रदान करते हैं
// सदस्य उन्हें एक्सेस और हेरफेर करने के लिए कार्य करता है।

// कुछ कंटेनर इस प्रकार हैं:

// वेक्टर (गतिशील सरणी)
// हमें रन टाइम पर ऐरे या ऑब्जेक्ट्स की सूची को परिभाषित करने की अनुमति दें
#include <vector>
string val;
vector<string> my_vector; // initialize the vector
cin >> val;
my_vector.push_back(val); // will push the value of 'val' into vector ("array") my_vector
my_vector.push_back(val); // will push the value into the vector again (now having two elements)

// एक वेक्टर के माध्यम से पुनरावृति करने के लिए हमारे पास 2 विकल्प हैं:
// या तो क्लासिक लूपिंग (वेक्टर के माध्यम से इंडेक्स 0 से उसके अंतिम इंडेक्स तक पुनरावृति):
for (int i = 0; i < my_vector.size(); i++) {
    cout << my_vector[i] << endl; // वेक्टर के तत्व तक पहुँचने के लिए हम ऑपरेटर का उपयोग कर सकते हैं []
}

// या एक पुनरावर्तक का उपयोग करना:
vector<string>::iterator it; // initialize the iterator for vector
for (it = my_vector.begin(); it != my_vector.end(); ++it) {
    cout << *it  << endl;
}

// सेट
// सेट कंटेनर हैं जो एक विशिष्ट क्रम के बाद अद्वितीय तत्वों को संग्रहीत करते हैं।
// सेट अद्वितीय मूल्यों को क्रमबद्ध क्रम में संग्रहीत करने के लिए एक बहुत ही उपयोगी कंटेनर है
// बिना किसी अन्य फ़ंक्शन या कोड के।

#include<set>
set<int> ST;    // Will initialize the set of int data type
ST.insert(30);  // Will insert the value 30 in set ST
ST.insert(10);  // Will insert the value 10 in set ST
ST.insert(20);  // Will insert the value 20 in set ST
ST.insert(30);  // Will insert the value 30 in set ST
// अब सेट के तत्व इस प्रकार हैं
// 10 20 30

// किसी तत्व को मिटाने के लिए
ST.erase(20); // मान 20 . के साथ तत्व मिटा देगा
// एसटी सेट करें: 10 30
// सेट के माध्यम से पुनरावृति करने के लिए हम पुनरावृत्तियों का उपयोग करते हैं
set<int>::iterator it;
for(it=ST.begin();it!=ST.end();it++) {
    cout << *it << endl;
}
// Output:
// 10
// 30

// पूरे कंटेनर को साफ करने के लिए हम कंटेनर_नाम.क्लियर () का उपयोग करते हैं
ST.clear();
cout << ST.size();  // will print the size of set ST
// आउटपुट: 0

// नोट: डुप्लिकेट तत्वों के लिए हम मल्टीसेट का उपयोग कर सकते हैं
// नोट: हैश सेट के लिए, unordered_set का उपयोग करें। वे अधिक कुशल हैं लेकिन
// आदेश को संरक्षित न करें। unordered_set C++11 के बाद से उपलब्ध है

// नक्शा
// मैप्स एक प्रमुख मूल्य के संयोजन द्वारा गठित तत्वों को संग्रहीत करता है
// और एक विशिष्ट क्रम के बाद एक मैप किया गया मान।

#include<map>
map<char, int> mymap;  // Will initialize the map with key as char and value as int

mymap.insert(pair<char,int>('A',1));
// Will insert value 1 for key A
mymap.insert(pair<char,int>('Z',26));
// Will insert value 26 for key Z

// To iterate
map<char,int>::iterator it;
for (it=mymap.begin(); it!=mymap.end(); ++it)
    std::cout << it->first << "->" << it->second << std::cout;
// आउटपुट:
// ए-> 1
// जेड-> 26

// कुंजी के अनुरूप मान ज्ञात करने के लिए
it = mymap.find('Z');
cout << it->second;

// आउटपुट: 26

// नोट: हैश मैप के लिए, unordered_map का उपयोग करें। वे अधिक कुशल हैं लेकिन करते हैं
// आदेश को संरक्षित नहीं करें। unordered_map C++11 के बाद से उपलब्ध है।

// गैर-आदिम मूल्यों (कस्टम वर्ग) की ऑब्जेक्ट कुंजियों वाले कंटेनरों की आवश्यकता होती है
// ऑब्जेक्ट में या फ़ंक्शन पॉइंटर के रूप में फ़ंक्शन की तुलना करें। पुरातन
// डिफ़ॉल्ट तुलनित्र हैं, लेकिन आप इसे ओवरराइड कर सकते हैं।
class Foo {
public:
    int j;
    Foo(int a) : j(a) {}
};
struct compareFunction {
    bool operator()(const Foo& a, const Foo& b) const {
        return a.j < b.j;
    }
};
// इसकी अनुमति नहीं है (हालांकि यह कंपाइलर के आधार पर भिन्न हो सकता है)
// एसटीडी :: नक्शा <फू, इंट> फूमैप;
std::map<Foo, int, compareFunction> fooMap;
fooMap[Foo(1)]  = 1;
fooMap.find(Foo(1)); //true


////////////////////////////////////
// लैम्ब्डा एक्सप्रेशन (सी ++ 11 और ऊपर)
////////////////////////////////////

// लैम्ब्डा एक अनाम फ़ंक्शन को परिभाषित करने का एक सुविधाजनक तरीका है
// वस्तु उस स्थान पर ठीक है जहां इसे लागू किया गया है या पारित किया गया है
// किसी फ़ंक्शन के लिए एक तर्क।

// उदाहरण के लिए, दूसरे का उपयोग करके जोड़े के वेक्टर को सॉर्ट करने पर विचार करें
// जोड़ी का मूल्य

vector<pair<int, int> > tester;
tester.push_back(make_pair(3, 6));
tester.push_back(make_pair(1, 9));
tester.push_back(make_pair(5, 0));

// लैम्ब्डा एक्सप्रेशन को सॉर्ट फ़ंक्शन के तीसरे तर्क के रूप में पास करें
// सॉर्ट <एल्गोरिदम> हेडर से है

sort(tester.begin(), tester.end(), [](const pair<int, int>& lhs, const pair<int, int>& rhs) {
        return lhs.second < rhs.second;
    });

// लैम्ब्डा एक्सप्रेशन के सिंटैक्स पर ध्यान दें,
// [] लैम्ब्डा में चर को "कैप्चर" करने के लिए प्रयोग किया जाता है
// "कैप्चर लिस्ट" परिभाषित करती है कि लैम्ब्डा के बाहर से फंक्शन बॉडी के अंदर क्या उपलब्ध होना चाहिए और कैसे।
// यह या तो हो सकता है:
// 1. एक मान: [x]
// 2. एक संदर्भ: [&x]
// 3. संदर्भ के अनुसार वर्तमान में कोई भी चर [&]
// 4. ३ के समान, लेकिन मूल्य से [=]
// उदाहरण:

vector<int> dog_ids;
// number_of_dogs = 3;
for(int i = 0; i < 3; i++) {
    dog_ids.push_back(i);
}

int weight[3] = {30, 50, 10};

// मान लें कि आप कुत्तों के वजन के अनुसार dog_ids को सॉर्ट करना चाहते हैं
// तो dog_ids अंत में बन जाना चाहिए: [२, ०, १]

// यहाँ वह जगह है जहाँ लैम्ब्डा के भाव काम आते हैं

sort(dog_ids.begin(), dog_ids.end(), [&weight](const int &lhs, const int &rhs) {
        return weight[lhs] < weight[rhs];
    });
// ध्यान दें कि हमने उपरोक्त उदाहरण में संदर्भ द्वारा "वजन" पर कब्जा कर लिया है।
// सी ++ में लैम्ब्डा पर अधिक: https://stackoverflow.com/questions/7627098/what-is-a-lambda-expression-in-c11

/////////////////////////////
// रेंज के लिए (सी ++ 11 और ऊपर)
/////////////////////////////

// आप एक कंटेनर पर लूप को पुनरावृत्त करने के लिए एक श्रेणी का उपयोग कर सकते हैं
int arr[] = {1, 10, 3};

for(int elem: arr){
    cout << elem << endl;
}

// आप "ऑटो" का उपयोग कर सकते हैं और कंटेनर के तत्वों के प्रकार के बारे में चिंता न करें
// उदाहरण के लिए:

for(auto elem: arr) {
    // Do something
}

/////////////////////
// मजेदार चीजें
/////////////////////

// सी ++ के पहलू जो नवागंतुकों (और यहां तक ​​​​कि कुछ दिग्गजों) के लिए आश्चर्यजनक हो सकते हैं।
// यह खंड, दुर्भाग्य से, बेतहाशा अधूरा है; सी ++ सबसे आसान में से एक है
// भाषाएं जिनके साथ अपने आप को पैर में गोली मारनी है।

// आप निजी तरीकों को ओवरराइड कर सकते हैं!
class Foo {
  virtual void bar();
};
class FooSub : public Foo {
  virtual void bar();  // Overrides Foo::bar!
};


// 0 == false == NULL (most of the time)!
bool* pt = new bool;
*pt = 0; // मान बिंदुओं को 'पीटी' द्वारा गलत पर सेट करता है।
pt = 0;  // 'पीटी' को अशक्त सूचक पर सेट करता है। दोनों पंक्तियाँ बिना किसी चेतावनी के संकलित हैं।

// nullptr उस समस्या में से कुछ को ठीक करने वाला है:
int* pt2 = new int;
*pt2 = nullptr; // Doesn't compile
pt2 = nullptr;  // Sets pt2 to null.

// बूल के लिए एक अपवाद बनाया गया है।
// यह आपको if(!ptr) के साथ नल पॉइंटर्स के लिए परीक्षण करने की अनुमति देता है,
// लेकिन परिणामस्वरूप आप सीधे बूल को नलप्टर असाइन कर सकते हैं!
*pt = nullptr;  // This still compiles, even though '*pt' is a bool!


// '=' != '=' != '='!
// कॉल फू :: फू (कॉन्स्ट फू एंड) या कुछ प्रकार (मूव शब्दार्थ देखें) कॉपी
// कंस्ट्रक्टर।
Foo f2;
Foo f1 = f2;

// कॉल फू :: फू (कॉन्स्ट फू एंड) या संस्करण, लेकिन केवल 'फू' भाग की प्रतिलिपि बनाता है
// 'फूसब'। 'fooSub' के किसी भी अतिरिक्त सदस्य को छोड़ दिया जाता है। यह कभी कभी
// भयानक व्यवहार को "ऑब्जेक्ट स्लाइसिंग" कहा जाता है।
FooSub fooSub;
Foo f1 = fooSub;

// Calls Foo::operator=(Foo&) or variant.
Foo f1;
f1 = f2;


////////////////////////////////////
// टुपल्स (सी ++ 11 और ऊपर)
////////////////////////////////////

#include<tuple>

// वैचारिक रूप से, टुपल्स पुराने डेटा संरचनाओं (सी-जैसी संरचना) के समान हैं
// लेकिन डेटा सदस्यों को नामित करने के बजाय,
// इसके तत्वों को टपल में उनके क्रम द्वारा एक्सेस किया जाता है।

// हम एक टपल के निर्माण के साथ शुरू करते हैं।
// मूल्यों को टपल में पैक करें
auto first = make_tuple(10, 'A');
const int maxN = 1e9;
const int maxL = 15;
auto second = make_tuple(maxN, maxL);

// Printing elements of 'first' tuple
cout << get<0>(first) << " " << get<1>(first) << '\n'; //prints : 10 A

// Printing elements of 'second' tuple
cout << get<0>(second) << " " << get<1>(second) << '\n'; // prints: 1000000000 15

// टपल को वेरिएबल में अनपैक करना

int first_int;
char first_char;
tie(first_int, first_char) = first;
cout << first_int << " " << first_char << '\n';  // prints : 10 A

// हम इस तरह टपल भी बना सकते हैं।

tuple<int, char, double> third(11, 'A', 3.14141);
// tuple_size टपल में तत्वों की संख्या लौटाता है (एक कॉन्स्टेक्स के रूप में)

cout << tuple_size<decltype(third)>::value << '\n'; // prints: 3

// tuple_cat सभी टुपल्स के तत्वों को एक ही क्रम में संयोजित करता है।

auto concatenated_tuple = tuple_cat(first, second, third);
// concatenated_tuple बन जाता है = (10, 'ए', 1e9, 15, 11, 'ए', 3.14141)

cout << get<0>(concatenated_tuple) << '\n'; // prints: 10
cout << get<3>(concatenated_tuple) << '\n'; // prints: 15
cout << get<5>(concatenated_tuple) << '\n'; // prints: 'A'


/////////////////////////////////
// लॉजिकल और बिटवाइज ऑपरेटर्स
////////////////////////////////

// सी ++ में अधिकांश ऑपरेटर अन्य भाषाओं की तरह ही हैं

// लॉजिकल ऑपरेटर्स

// सी ++ बूलियन अभिव्यक्तियों के लिए शॉर्ट-सर्किट मूल्यांकन का उपयोग करता है, यानी, दूसरा तर्क निष्पादित किया जाता है या
// केवल तभी मूल्यांकन किया जाता है जब पहला तर्क अभिव्यक्ति के मूल्य को निर्धारित करने के लिए पर्याप्त नहीं है

true && false // निष्पादित करता है **तार्किक और** असत्य उत्पन्न करने के लिए
true || false // सत्य उत्पन्न करने के लिए **तार्किक या** करता है
! true        // प्रदर्शन करता है **तार्किक नहीं** झूठा उत्पन्न करने के लिए

// प्रतीकों का उपयोग करने के बजाय समकक्ष कीवर्ड का उपयोग किया जा सकता है
true and false // प्रदर्शन करता है **तार्किक और ** गलत उत्पन्न करने के लिए
true or false  // सत्य उत्पन्न करने के लिए **तार्किक या ** करता है
not true       // निष्पादित करता है **तार्किक नहीं ** असत्य उत्पन्न करने के लिए

// बिटवाइज ऑपरेटर्स

// **<<** लेफ्ट शिफ्ट ऑपरेटर
// << बिट्स को बाईं ओर शिफ्ट करता है
4 << 1 // 8 देने के लिए 4 के बिट्स को 1 से बायीं ओर शिफ्ट करता है
// x << n को x * 2^n . के रूप में माना जा सकता है


// **>>** राइट शिफ्ट ऑपरेटर
// >> बिट्स को दाईं ओर शिफ्ट करता है
4 >> 1 // २ देने के लिए ४ के बिट्स को १ से दायीं ओर शिफ्ट करता है
// x >> n को x / 2^n . के रूप में माना जा सकता है

~4    // Performs a bitwise not
4 | 3 // Performs bitwise or
4 & 3 // Performs bitwise and
4 ^ 3 // Performs bitwise xor

// समतुल्य कीवर्ड हैं
compl 4    // Performs a bitwise not
4 bitor 3  // Performs bitwise or
4 bitand 3 // Performs bitwise and
4 xor 3    // Performs bitwise xor
```

अग्रिम पठन:

* एक अप-टू-डेट भाषा संदर्भ [सीपीपी संदर्भ](http://cppreference.com/w/cpp) पर पाया जा सकता है।
* अतिरिक्त संसाधन [CPlusPlus](http://cplusplus.com) पर मिल सकते हैं।
* [TheChernoProject - C++](https://www.youtube.com/playlist?list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb) पर भाषा की बुनियादी बातों और कोडिंग परिवेश को सेट करने वाला एक ट्यूटोरियल उपलब्ध है।