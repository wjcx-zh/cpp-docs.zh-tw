---
title: "match_results 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: regex/std::match_results
dev_langs: C++
helpviewer_keywords: match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f0fa4ea48a9947492ee4ce53f33450d1944d6d3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="matchresults-class"></a>match_results 類別
保留子相符項目的序列。  
  
## <a name="syntax"></a>語法  
```  
class match_results {  
   public:  
   explicit match_results(const Alloc& alloc = Alloc());
   match_results(const match_results& right);
   match_results& operator=(const match_results& right);
   difference_type position(size_type sub = 0) const;
   difference_type length(size_type sub = 0) const;
   string_type str(size_type sub = 0) const;
   const_reference operator[](size_type n) const;
   const_reference prefix() const;
   const_reference suffix() const;
   const_iterator begin() const;
   const_iterator end() const;
   template <class OutIt>  
   OutIt format(OutIt out,  
   const string_type& fmt, match_flag_type flags = format_default) const;
   string_type format(const string_type& fmt,  
   match_flag_type flags = format_default) const;
   allocator_type get_allocator() const;
   void swap(const match_results& other) throw();
   size_type size() const;
   size_type max_size() const;
   bool empty() const;
   typedef sub_match<BidIt>  
   value_type;  
   typedef const typename Alloc::const_reference const_reference;  
   typedef const_reference reference;  
   typedef T0 const_iterator;  
   typedef const_iterator iterator;  
   typedef typename iterator_traits<BidIt>::difference_type difference_type;  
   typedef typename Alloc::size_type size_type;  
   typedef Alloc allocator_type;  
   typedef typename iterator_traits<BidIt>::value_type char_type;  
   typedef basic_string<char_type> string_type;  
   };  
```  
#### <a name="parameters"></a>參數  
 `BidIt`  
 子相符項目的迭代器類型。  
  
 `Alloc`  
 管理儲存體的配置器類型。  
  
## <a name="remarks"></a>備註  
 此樣板類別所描述的物件可控制規則運算式搜尋所產生之 `sub_match<BidIt>` 類型項目的不可修改序列。 每個項目會指向符合對應至該項目之擷取群組的子序列。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<regex>  
  
 **命名空間：** std  
  
##  <a name="allocator_type"></a>  match_results::allocator_type  
 管理儲存體的配置器類型。  
  
```  
typedef Alloc allocator_type;  
```  
  
### <a name="remarks"></a>備註  
 typedef 是範本引數 `Alloc`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_allocator_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="begin"></a>  match_results::begin  
 指定子相符項目序列的開頭。  
  
```  
const_iterator begin() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式傳回的隨機存取迭代器，指向序列的第一個項目 (或空序列結尾以外的位置)。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_begin.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="char_type"></a>  match_results::char_type  
 元素的類型。  
  
```  
typedef typename iterator_traits<BidIt>::value_type char_type;  
```  
  
### <a name="remarks"></a>備註  
 這個 typedef 與 `iterator_traits<BidIt>::value_type`類型同義，後者是搜尋到之字元序列的項目類型。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_char_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="const_iterator"></a>  match_results::const_iterator  
 子相符項目的 const 迭代器類型。  
  
```  
typedef T0 const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此 typedef 所描述的物件可做為受控制序列的常數隨機存取迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_const_iterator.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="const_reference"></a>  match_results::const_reference  
 元素 const 參考的類型。  
  
```  
typedef const typename Alloc::const_reference const_reference;  
```  
  
### <a name="remarks"></a>備註  
 typedef 所說明的物件可作為受控制序列之元素的常數參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_const_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="difference_type"></a>  match_results::difference_type  
 迭代器差值的類型。  
  
```  
typedef typename iterator_traits<BidIt>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>備註  
 Typedef 是 `iterator_traits<BidIt>::difference_type`類型的同義字；它描述一個物件，可以代表指向受控制序列中項目之任何兩個迭代器間的差值。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_difference_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="empty"></a>  match_results::empty  
 測試是否沒有任何子相符項目。  
  
```  
bool empty() const;
```  
  
### <a name="remarks"></a>備註  
 只有在規則運算式搜尋失敗時，此成員函式才會傳回 true。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_empty.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="end"></a>  match_results::end  
 指定子相符項目序列的結尾。  
  
```  
const_iterator end() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回指向序列結尾之外的迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_end.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="format"></a>  match_results::format  
 格式子相符項目。  
  
```  
template <class OutIt>  
OutIt format(OutIt out,  
    const string_type& fmt, match_flag_type flags = format_default) const;

 
string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```  
  
### <a name="parameters"></a>參數  
 `OutIt`  
 輸出迭代器類型。  
  
 `out`  
 要寫入的輸出資料流。  
  
 `fmt`  
 格式字串。  
  
 `flags`  
 格式旗標。  
  
### <a name="remarks"></a>備註  
 受 `fmt` 格式的控制下，每個成員函式產生格式化文字。 第一個成員函式將格式化文字寫入其引數 `out` 所定義的序列，並傳回 `out`。 第二個成員函式會傳回保存格式化文件複本的字串物件。  
  
 若要產生格式化文字， 格式字串中的常值文字通常會複製到目標序列。 格式字串中的每個逸出序列由所代表的文字取代。 複製和取代的詳細資料受到傳遞至函式的格式旗標控制。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_format.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="get_allocator"></a>  match_results::get_allocator  
 傳回已儲存的配置器。  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 `*this` 用來配置其 `sub_match` 的配置器物件複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_get_allocator.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="iterator"></a>  match_results::iterator  
 子相符項目的迭代器類型。  
  
```  
typedef const_iterator iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型說明可作為受控制序列之隨機存取迭代器的物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_iterator.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="length"></a>  match_results::length  
 傳回子相符項目的長度。  
  
```  
difference_type length(size_type sub = 0) const;
```  
  
### <a name="parameters"></a>參數  
 `sub`  
 子相符項目的索引。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 `(*this)[sub].length()`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_length.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="match_results"></a>  match_results::match_results  
 建構物件。  
  
```  
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```  
  
### <a name="parameters"></a>參數  
 `alloc`  
 要儲存的配置器物件。  
  
 `right`  
 要複製的 match_results 物件。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會建構不含子相符項目的 `match_results` 物件。 第二個建構函式會建構是 `right` 之複本的 `match_results` 物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="max_size"></a>  match_results::max_size  
 取得最大子相符項目數。  
  
```  
size_type max_size() const;
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回物件可以控制之最長序列的長度。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_max_size.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="op_eq"></a>  match_results::operator=  
 複製 match_results 物件。  
  
```  
match_results& operator=(const match_results& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要複製的 match_results 物件。  
  
### <a name="remarks"></a>備註  
 成員運算子會將 `*this` 所控制的序列取代為 `right` 所控制之序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_operator_as.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="op_at"></a>  match_results::operator[]  
 存取子物件。  
  
```  
const_reference operator[](size_type n) const;
```  
  
### <a name="parameters"></a>參數  
 `n`  
 子相符項目的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回受控制序列之項目 `n` 的參考；如果 `sub_match` 或擷取群組 `size() <= n` 不是比對的一部分，則傳回空白 `n` 物件的參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_operator_br.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="position"></a>  match_results::position  
 取得子群組的起始位移。  
  
```  
difference_type position(size_type sub = 0) const;
```  
  
### <a name="parameters"></a>參數  
 `sub`  
 子相符項目的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回 `std::distance(prefix().first, (*this)[sub].first)`，也就是從目標序列中的第一個字元，到受控制序列的 `n` 項目所指向的子相符項目中第一個字元之間的距離。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_position.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="prefix"></a>  match_results::prefix  
 取得第一個子相符項目之前的序列。  
  
```  
const_reference prefix() const;
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回 `sub_match<BidIt>` 類型物件的參考，以指向起始於目標序列開頭並結束於 `(*this)[0].first`的字元序列，也就是指向相符子序列之前的文字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_prefix.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="reference"></a>  match_results::reference  
 元素參考的類型。  
  
```  
typedef const_reference reference;  
```  
  
### <a name="remarks"></a>備註  
 這個類型與類型 `const_reference`同義。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="size"></a>  match_results::size  
 計算子相符項目數。  
  
```  
size_type size() const;
```  
  
### <a name="remarks"></a>備註  
 如果用於搜尋的數目超過規則運算式中的擷取群組數目，此成員函式會傳回 1；如果不進行搜尋，則會傳回 0。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_size.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="size_type"></a>  match_results::size_type  
 子相符項目計數的類型。  
  
```  
typedef typename Alloc::size_type size_type;  
```  
  
### <a name="remarks"></a>備註  
 這個類型與類型 `Alloc::size_type`同義。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_size_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="str"></a>  match_results::str  
 傳回子相符項目。  
  
```  
string_type str(size_type sub = 0) const;
```  
  
### <a name="parameters"></a>參數  
 `sub`  
 子相符項目的索引。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 `string_type((*this)[sub])`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_str.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="string_type"></a>  match_results::string_type  
 字串的類型。  
  
```  
typedef basic_string<char_type> string_type;  
```  
  
### <a name="remarks"></a>備註  
 這個類型與類型 `basic_string<char_type>`同義。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_string_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="suffix"></a>  match_results::suffix  
 取得最後一個子相符項目之後的序列。  
  
```  
const_reference suffix() const;
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回 `sub_match<BidIt>` 類型物件的參考，以指向起始於 `(*this)[size() - 1].second` 並結束於目標序列結尾的字元序列，也就是指向相符子序列之後的文字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_suffix.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="swap"></a>  match_results::swap  
 交換兩個 match_results 物件。  
  
```  
void swap(const match_results& right) throw();
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要交換的 match_results 物件。  
  
### <a name="remarks"></a>備註  
 此成員函式會定時交換 `*this` 和 `right` 的內容，但不會擲回例外狀況。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_swap.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="value_type"></a>  match_results::value_type  
 子對應的類型。  
  
```  
typedef sub_match<BidIt> value_type;  
```  
  
### <a name="remarks"></a>備註  
 typedef 與類型 `sub_match<BidIt>`同義。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__match_results_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
## <a name="see-also"></a>請參閱  
 [\<regex>](../standard-library/regex.md)


