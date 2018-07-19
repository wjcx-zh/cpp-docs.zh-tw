---
title: __raise |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __raise
- __raise_cpp
dev_langs:
- C++
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a95f012b36e30c171fde1cbc8d28a21a074e281
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942688"
---
# <a name="raise"></a>__raise
強調事件的呼叫位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
__raise method-declarator;  
  
```  
  
## <a name="remarks"></a>備註  
 在 Managed 程式碼中，只能從已定義的類別內引發事件。 請參閱[事件](../windows/event-cpp-component-extensions.md)如需詳細資訊。  
  
 關鍵字 **__raise**會導致當您呼叫與事件，就會發出錯誤。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## <a name="example"></a>範例  
  
```cpp 
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