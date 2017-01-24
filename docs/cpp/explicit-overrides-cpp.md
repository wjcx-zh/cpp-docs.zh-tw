---
title: "明確覆寫 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "衍生類別, 虛擬函式"
  - "虛擬函式的明確覆寫"
  - "明確虛擬函式覆寫"
  - "覆寫, 函式"
  - "虛擬函式, 明確覆寫"
ms.assetid: ee583234-5cda-4e90-b55e-3f9fbf079ced
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 明確覆寫 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 如果在兩個或多個[介面](../cpp/interface.md)中宣告同一個虛擬函式，且若類別衍生自這些介面，您可以明確覆寫每個虛擬函式。  
  
 如需深入了解使用新 Managed 語法的 Managed 程式碼中的明確覆寫，請參閱[明確覆寫](../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 **END Microsoft 特定的**  
  
## 範例  
 下列程式碼範例示範如何使用明確覆寫：  
  
```  
// deriv_ExplicitOverrides.cpp  
// compile with: /GR  
extern "C" int printf_s(const char *, ...);  
  
__interface IMyInt1 {  
   void mf1();  
   void mf1(int);  
   void mf2();  
   void mf2(int);  
};  
  
__interface IMyInt2 {  
   void mf1();  
   void mf1(int);  
   void mf2();  
   void mf2(int);  
};  
  
class CMyClass : public IMyInt1, public IMyInt2 {  
public:  
   void IMyInt1::mf1() {  
      printf_s("In CMyClass::IMyInt1::mf1()\n");  
   }  
  
   void IMyInt1::mf1(int) {  
      printf_s("In CMyClass::IMyInt1::mf1(int)\n");  
   }  
  
   void IMyInt1::mf2();  
   void IMyInt1::mf2(int);  
  
   void IMyInt2::mf1() {  
      printf_s("In CMyClass::IMyInt2::mf1()\n");  
   }  
  
   void IMyInt2::mf1(int) {  
         printf_s("In CMyClass::IMyInt2::mf1(int)\n");  
   }  
  
   void IMyInt2::mf2();  
   void IMyInt2::mf2(int);  
};  
  
void CMyClass::IMyInt1::mf2() {  
   printf_s("In CMyClass::IMyInt1::mf2()\n");  
}  
  
void CMyClass::IMyInt1::mf2(int) {  
   printf_s("In CMyClass::IMyInt1::mf2(int)\n");  
}  
  
void CMyClass::IMyInt2::mf2() {  
   printf_s("In CMyClass::IMyInt2::mf2()\n");  
}  
  
void CMyClass::IMyInt2::mf2(int) {  
   printf_s("In CMyClass::IMyInt2::mf2(int)\n");  
}  
  
int main() {  
   IMyInt1 *pIMyInt1 = new CMyClass();  
   IMyInt2 *pIMyInt2 = dynamic_cast<IMyInt2 *>(pIMyInt1);  
  
   pIMyInt1->mf1();  
   pIMyInt1->mf1(1);  
   pIMyInt1->mf2();  
   pIMyInt1->mf2(2);  
   pIMyInt2->mf1();  
   pIMyInt2->mf1(3);  
   pIMyInt2->mf2();  
   pIMyInt2->mf2(4);  
  
   // Cast to a CMyClass pointer so that the destructor gets called  
      CMyClass *p = dynamic_cast<CMyClass *>(pIMyInt1);  
      delete p;  
}  
```  
  
  **在 CMyClass::IMyInt1::mf1\(\)**  
**在 CMyClass::IMyInt1::mf1\(int\)**  
**在 CMyClass::IMyInt1::mf2\(\)**  
**在 CMyClass::IMyInt1::mf2\(int\)**  
**在 CMyClass::IMyInt2::mf1\(\)**  
**在 CMyClass::IMyInt2::mf1\(int\)**  
**在 CMyClass::IMyInt2::mf2\(\)**  
**在 CMyClass::IMyInt2::mf2\(int\)**   
## 請參閱  
 [繼承](../cpp/inheritance-cpp.md)