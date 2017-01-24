---
title: "basic_ostream 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::basic_ostream"
  - "std.basic_ostream"
  - "ostream/std::basic_ostream"
  - "basic_ostream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ostream 類別"
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
caps.latest.revision: 24
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_ostream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此範本類別所說明的物件，可控制如何將項目和編碼物件插入具有類型 **Elem** \(也稱為 [char\_type](../Topic/basic_ios::char_type.md)\) 之項目的資料流緩衝區；該類型的字元特性由類別 **Tr** \(也稱為 [traits\_type](../Topic/basic_ios::traits_type.md)\) 所決定。  
  
## 語法  
  
```  
  
template <class   
_Elem  
, class   
_Tr  
 = char  
_  
traits<Elem> >  
   class basic  
_  
ostream  
       : virtual public basic  
_  
ios<  
_Elem  
,   
_Tr  
>  
  
```  
  
#### 參數  
 `_Elem`  
 `char_type`。  
  
 `_Tr`  
 字元 `traits_type`。  
  
## 備註  
 大部分多載 [operator\<\<](../Topic/basic_ostream::operator%3C%3C.md) 的成員函式為格式化的輸出函式。 它們遵循下列模式：  
  
```  
iostate state = goodbit;  
const sentry ok( *this );  
if ( ok )  
   {try  
      {<convert and insert elements  
      accumulate flags in state> }  
   catch ( ... )  
      {try  
        {setstate( badbit ); }  
      catch ( ... )  
        {}  
      if ( ( exceptions( ) & badbit ) != 0 )  
        throw; }}  
width( 0 );    // Except for operator<<(Elem)  
setstate( state );  
return ( *this );  
```  
  
 其他兩個成員函式是未格式化的輸出函式。 它們遵循下列模式：  
  
```  
iostate state = goodbit;  
const sentry ok( *this );  
if ( !ok )  
   state |= badbit;  
else  
   {try  
      {<obtain and insert elements  
      accumulate flags in state> }  
   catch ( ... )  
      {try  
         {setstate( badbit ); }  
      catch ( ... )  
         {}  
      if ( ( exceptions( ) & badbit ) != 0 )  
         throw; }}  
setstate( state );  
return ( *this );  
```  
  
 如果在插入項目時遭遇失敗，則這兩個函式群組都會呼叫 [setstate](../Topic/basic_ios::setstate.md)**\(badbit\)**。  
  
 類別 basic\_istream\<**Elem**, **Tr**\> 的物件只會儲存類別 [basic\_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr\>** 的虛擬公用基底物件。  
  
## 範例  
 請參閱範例 [basic\_ofstream 類別](../standard-library/basic-ofstream-class.md) 若要深入了解輸出資料流。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_ostream](../Topic/basic_ostream::basic_ostream.md)|建構 `basic_ostream` 物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[flush](../Topic/basic_ostream::flush.md)|清除緩衝區。|  
|[put](../Topic/basic_ostream::put.md)|將字元置入資料流中。|  
|[seekp](../Topic/basic_ostream::seekp.md)|重設輸出資料流中的位置。|  
|[sentry](../Topic/basic_ostream::sentry.md)|此巢狀的類別會描述物件，該物件的宣告會將格式化輸出函式和未格式化輸出函式結構化。|  
|[swap](../Topic/basic_ostream::operator=.md)|用所提供的 `basic_ostream` 物件的值交換這個 `basic_ostream` 物件中的值。|  
|[tellp](../Topic/basic_ostream::tellp.md)|報告輸出資料流中的位置。|  
|[寫入](../Topic/basic_ostream::write.md)|將字元置入資料流中。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/basic_ostream::operator=.md)|將提供的 `basic_ostream` 物件參數值指派為這個物件。|  
|[operator\<\<](../Topic/basic_ostream::operator%3C%3C.md)|寫入資料流。|  
  
## 需求  
 **標頭：**\<ostream\>  
  
 **命名空間：**std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)