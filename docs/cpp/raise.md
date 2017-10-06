---
title: "__raise |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __raise
- __raise_cpp
dev_langs:
- C++
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 0303198f352b97cf84a97d63dce18055e63622b1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="raise"></a>__raise
強調事件的呼叫位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
__raise   
method-declarator  
;  
  
```  
  
## <a name="remarks"></a>備註  
 在 Managed 程式碼中，只能從已定義的類別內引發事件。 請參閱[事件](../windows/event-cpp-component-extensions.md)如需詳細資訊。  
  
 如果您呼叫的不是事件，則關鍵字 `__raise` 會導致錯誤發出。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## <a name="example"></a>範例  
  
```  
// EventHandlingRef_raise.cpp  
struct E {  
   __event void func1();  
   void func1(int) {}  
  
   void func2() {}  
  
   void b() {  
      __raise func1();  
      __raise func1(1);  // C3745: 'int Event::bar(int)':   
                         // only an event can be 'raised'  
      __raise func2();   // C3745  
   }  
};  
  
int main() {  
   E e;  
   __raise e.func1();  
   __raise e.func1(1);  // C3745  
   __raise e.func2();   // C3745  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [事件處理](../cpp/event-handling.md)   
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)
