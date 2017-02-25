---
title: "basic_istream 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_istream"
  - "istream/std::basic_istream"
  - "std::basic_istream"
  - "std.basic_istream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_istream 類別"
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# basic_istream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

說明的物件可控制如何從具有 `Elem` 類型 \(也稱為 [char\_type](../Topic/basic_ios::char_type.md)\) 之項目的資料流緩衝區擷取項目及編碼物件；而該類型的字元特性由類別 *Tr* \(也稱為 [traits\_type](../Topic/basic_ios::traits_type.md)\) 所決定。  
  
## 語法  
  
```  
  
     template <class   
     Elem  
     , class   
     Tr  
      = char  
     _  
     traits<  
     Elem  
     > >  
class basic_istream  
   : virtual public basic_ios<Elem, Tr>  
```  
  
## 備註  
 大部分多載 [operator\>\>](../Topic/basic_istream::operator%3E%3E.md) 的成員函式，為格式化的輸入函式。  它們遵循下列模式：  
  
```  
iostate state = goodbit;  
const sentry ok(*this);  
if (ok)  
    {try  
        {<extract elements and convert  
        accumulate flags in state  
        store a successful conversion> }  
    catch (...)  
        {try  
            {setstate(badbit); }  
        catch (...)  
            {}  
        if ((exceptions( ) & badbit) != 0)  
            throw; }}  
setstate(state);  
return (*this);  
```  
  
 許多其他的成員函式為未經格式化的輸入函式。  它們遵循下列模式：  
  
```  
iostate state = goodbit;  
count = 0;    // the value returned by gcount  
const sentry ok(*this, true);  
if (ok)  
    {try  
        {<extract elements and deliver  
        count extracted elements in count  
        accumulate flags in state> }  
    catch (...)  
        {try  
            {setstate(badbit); }  
        catch (...)  
            {}  
        if ((exceptions( ) & badbit) != 0)  
            throw; }}  
setstate(state);  
```  
  
 如果在擷取項目時遇到檔案結尾，則這兩種函式群組都會呼叫 [setstate](../Topic/basic_ios::setstate.md)\(**eofbit**\)。  
  
 類別 `basic_istream`\<`Elem`, *Tr*\> 的物件會儲存：  
  
-   類別 [basic\_ios](../standard-library/basic-ios-class.md)\<`Elem`, *Tr*\>`.` 的虛擬公開基底物件。  
  
-   最後一個未經格式化的輸入作業之擷取計數 \(在先前的程式碼中稱為 **count**\)。  
  
## 範例  
 若要深入了解輸入資料流，請參閱 [basic\_ifstream 類別](../standard-library/basic-ifstream-class.md)的範例。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_istream](../Topic/basic_istream::basic_istream.md)|建構類型 `basic_istream` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[gcount](../Topic/basic_istream::gcount.md)|傳回最後一個未經格式化的輸入期間，讀取的字元數。|  
|[get](../Topic/basic_istream::get.md)|從輸入資料流讀取一或多個字元。|  
|[getline](../Topic/basic_istream::getline.md)|從輸入資料流讀取一行。|  
|[略過](../Topic/basic_istream::ignore.md)|導致從目前的讀取位置略過一些項目。|  
|[peek](../Topic/basic_istream::peek.md)|傳回要讀取的下一個字元。|  
|[putback](../Topic/basic_istream::putback.md)|將指定的字元放入資料流。|  
|[read](../Topic/basic_istream::read.md)|從資料流讀取指定的字元數，並將其儲存在陣列中。|  
|[readsome](../Topic/basic_istream::readsome.md)|只從緩衝區讀取。|  
|[seekg](../Topic/basic_istream::seekg.md)|移動資料流中的讀取位置。|  
|[sentry](../Topic/basic_istream::sentry.md)|此巢狀類別會描述物件，該物件的宣告會建構格式化的輸入函式以及未經格式化的輸入函式。|  
|[交換](../Topic/basic_istream::swap.md)|以 `basic_istream` 物件交換所提供的 `basic_istream` 物件參數。|  
|[sync](../Topic/basic_istream::sync.md)|同步處理與資料流緩衝區的資料流相關聯的輸入裝置。|  
|[tellg](../Topic/basic_istream::tellg.md)|回報在資料流中目前的讀取位置。|  
|[unget](../Topic/basic_istream::unget.md)|將最近讀取的字元放回資料流。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \>\>](../Topic/basic_istream::operator%3E%3E.md)|呼叫輸入資料流上的函式，或從輸入資料流讀取經格式化的資料。|  
|[operator\=](../Topic/basic_istream::operator=.md)|將位於運算子右側的 `basic_istream` 指派給此物件。  這是一個移動指派，涉及不會留下複本的 `rvalue` 參考。|  
  
## 需求  
 **標頭：**\<istream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)