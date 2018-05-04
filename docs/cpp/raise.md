---
title: __raise |Microsoft 文件
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
ms.openlocfilehash: 93bd00c89df69d655f42c06509ef0360eff0c092
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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