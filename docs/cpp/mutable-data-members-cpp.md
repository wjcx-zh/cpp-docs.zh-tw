---
title: "可變動的資料成員 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "mutable_cpp"
  - "mutable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mutable 關鍵字 [C++]"
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 可變動的資料成員 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個關鍵字只能套用至非靜態和非常數類別的資料成員。  如果資料成員宣告為 `mutable`，則可從 **const** 成員函式指派值給這個資料成員。  
  
## 語法  
  
```  
  
mutable member-variable-declaration;  
```  
  
## 備註  
 例如，下列程式碼會在沒有錯誤的情況下完成編譯，因為 `m_accessCount` 已宣告為 `mutable`，因此，即使 `GetFlag` 是常數成員函式，`GetFlag` 也可以進行修改。  
  
```  
// mutable.cpp  
class X  
{  
public:  
   bool GetFlag() const  
   {  
      m_accessCount++;  
      return m_flag;  
   }  
private:  
   bool m_flag;  
   mutable int m_accessCount;  
};  
  
int main()  
{  
}  
```  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)