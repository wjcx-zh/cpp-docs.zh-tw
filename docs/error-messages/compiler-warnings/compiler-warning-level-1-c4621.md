---
title: "編譯器警告 (層級 1) C4621 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4621"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4621"
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4621
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到型別 'type' 後置格式的 '\-\- 運算子'，已改用前置格式  
  
 未定義此提供型別的後置遞減 \(Decrement\) 運算子。  編譯器使用多載的後置運算子。  
  
 定義後置的 `--` 運算子即可避免此警告。  如下所示建立一個有兩個引數的 `--` 運算子：  
  
```  
// C4621.cpp  
// compile with: /W1  
class A  
{  
public:  
   A(int nData) : m_nData(nData)  
   {  
   }  
  
   A operator--()  
   {  
      m_nData -= 1;  
      return *this;  
   }  
  
   // A operator--(int)  
   // {  
   //    A tmp = *this;  
   //    m_nData -= 1;  
   //    return tmp;  
   // }  
  
private:  
   int m_nData;  
};  
  
int main()  
{  
   A a(10);  
   --a;  
   a--;   // C4621  
}  
```