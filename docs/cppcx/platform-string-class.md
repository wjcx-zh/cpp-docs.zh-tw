---
title: "Platform::String 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String"
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::String 類別
用來代表文字之 Unicode 字元的循序集合。 如需詳細資訊與範例，請參閱[字串](../cppcx/strings-c-cx.md)。  
  
## 語法  
  
```cpp  
  
public ref class String sealed : Object,  
    IDisposable,  
    IEquatable,  
    IPrintable  
```  
  
## 迭代器  
 有兩個 Iterator 函式 \(不是字串類別的成員\) 可與 `std::for_each` 樣板搭配使用，以列舉 String 物件中的字元。  
  
|成員|描述|  
|--------|--------|  
|`const char16* begin(String^ s)`|讓指標回到指定 String 物件的開頭。|  
|`const char16* end(String^ s)`|讓指標回到指定 String 物件的結尾之後。|  
  
## Members  
 字串類別繼承自 Object 以及 IDisposable、IEquatable 與 IPrintable 介面。  
  
 字串類別也有下列幾種型别的成員。  
  
 **建構函式**  
  
|成員|描述|  
|--------|--------|  
|[String::String 建構函式](../cppcx/string-string-constructor.md)|初始化字串類別的新執行個體。|  
  
 **方法**  
  
 字串類別會從 [Platform::Object 類別](../cppcx/platform-object-class.md) 繼承 Equals\(\)、Finalize\(\)、GetHashCode\(\)、GetType\(\)、MemberwiseClose\(\) 與 ToString\(\) 等方法。 字串也有下列方法。  
  
|方法|描述|  
|--------|--------|  
|[String::Begin 方法](../cppcx/string-begin-method.md)|讓指標回到目前字串的開頭。|  
|[String::CompareOrdinal 方法](../cppcx/string-compareordinal-method.md)|評估物件所代表之兩個字串值中的對應字元數值，藉以比較兩個 `String` 物件。|  
|[String::Concat 方法](../cppcx/string-concat-method.md)|串連兩個 String 物件的值。|  
|[String::Data 方法](../cppcx/string-data-method.md)|讓指標回到目前字串的開頭。|  
|[String::Dispose 方法](../cppcx/string-dispose-method.md)|釋放或釋出資源。|  
|[String::End 方法](../cppcx/string-end-method.md)|讓指標回到目前字串的結尾之後。|  
|[String::Equals 方法](../cppcx/string-equals-method.md)|指出指定的物件是否等同於目前的物件。|  
|[String::GetHashCode 方法](../cppcx/string-gethashcode-method.md)|傳回這個執行個體的雜湊碼。|  
|[String::IsEmpty 方法](../cppcx/string-isempty-method.md)|指出目前 String 物件是否為空。|  
|[String::IsFastPass 方法](../cppcx/string-isfastpass-method.md)|指出目前 String 物件是否參與「*快速傳遞*」\(Fast Pass\) 作業。 在快速傳遞作業時，參考計數會暫停。|  
|[String::Length 方法](../cppcx/string-length-method.md)|擷取目前 String 物件的長度。|  
|[String::ToString 方法](../cppcx/string-tostring-method-c-cx.md)|傳回值與目前字串相同的 String 物件。|  
  
 **屬性**  
  
 字串類別具有下列屬性。  
  
|成員|描述|  
|--------|--------|  
|[String::operator\=\= 運算子](../cppcx/string-operator-equality-operator-c-cx.md)|指出兩個指定的 String 物件是否具有相同的值。|  
|[operator\+ 運算子](../cppcx/string-operator-decrementoperator.md)|將兩個 String 物件串連成新的 String 物件。|  
|[String::operator\> 運算子](../cppcx/string-operator-greater-than-operator-c-cx.md)|指出其中一個 String 物件的值是否大於另一個 String 物件的值。|  
|[String::operator\>\= 運算子](../cppcx/string-operator-greater-than-or-equals-c-cx.md)|指出其中一個 String 物件的值是否大於或等於另一個 String 物件的值。|  
|[String::operator\!\= 運算子](../cppcx/string-operator-inequality-operator-c-cx.md)|指出兩個指定的 String 物件是否具有不同的值。|  
|[String::operator\< 運算子](../cppcx/string-operator-less-than-operator-c-cx.md)|指出其中一個 String 物件的值是否小於另一個 String 物件的值。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭**：vccorlib.h \(預設包含\)  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)