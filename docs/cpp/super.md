---
title: "__super |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __super_cpp
dev_langs:
- C++
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 64600f8cf642b0c7906873a73aa4da41897a57f5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="super"></a>__super
**Microsoft 特定的**  
  
 可讓您明確陳述您要呼叫將覆寫之函式的基底類別實作。  
  
## <a name="syntax"></a>語法  
  
```  
  
__super::  
member_function  
();  
  
```  
  
## <a name="remarks"></a>備註  
 多載解析階段會考量所有可存取的基底類別方法，並且提供最佳相符結果的函式即為將會呼叫的函式。  
  
 `__super` 只能出現在成員函式的主體中。  
  
 `__super` 不能與 using 宣告搭配使用。 請參閱[using 宣告](../cpp/using-declaration.md)如需詳細資訊。  
  
 透過推出[屬性](../windows/cpp-attributes-reference.md)插入程式碼，您的程式碼可能會包含的名稱可能不知道，但其中包含您想要呼叫的方法的一個或多個基底的類別。  
  
## <a name="example"></a>範例  
  
```  
// deriv_super.cpp  
// compile with: /c  
struct B1 {  
   void mf(int) {}  
};  
  
struct B2 {  
   void mf(short) {}  
  
   void mf(char) {}  
};  
  
struct D : B1, B2 {  
   void mf(short) {  
      __super::mf(1);   // Calls B1::mf(int)  
      __super::mf('s');   // Calls B2::mf(char)  
   }  
};  
```  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)
