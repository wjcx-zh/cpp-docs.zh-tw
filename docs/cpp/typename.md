---
title: "typename | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "typename"
  - "typename_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "typename 樣板規範"
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# typename
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

告知編譯器未知的識別項是一種類型。  
  
## 語法  
  
```  
  
typename identifier;  
```  
  
## 備註  
 請只在樣板定義中使用此關鍵字。  
  
 如果名稱是取決於樣板引數的限定名稱，則必須使用這個關鍵字，如果限定名稱不具相依性，則可以選擇性使用此關鍵字。  如需詳細資訊，請參閱[範本和名稱解析](../cpp/templates-and-name-resolution.md)。  
  
 **typename** 只可以由樣板宣告或定義中的任何類型使用。  除非是做為範本基底類別的樣板引數，否則不允許出現在基底類別清單中。  
  
```  
template <class T>  
class C1 : typename T::InnerType // Error - typename not allowed.  
{};  
template <class T>  
class C2 : A<typename T::InnerType>  // typename OK.  
{};  
```  
  
 **typename** 關鍵字也可以在樣板參數清單的 **class** 位置中使用。  例如，以下為相同的陳述式：  
  
```  
template<class T1, class T2>...  
template<typename T1, typename T2>...  
```  
  
## 範例  
  
```  
// typename.cpp  
template<class T> class X  
{  
   typename T::Y m_y;   // treat Y as a type  
};  
  
int main()  
{  
}  
```  
  
## 請參閱  
 [樣板](../cpp/templates-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)