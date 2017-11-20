---
title: "__uuidof 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
dev_langs: C++
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54a21ead5f47bd931bae912cb4ca28a8d900a75b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="uuidof-operator"></a>__uuidof 運算子
**Microsoft 特定的**  
  
 擷取附加至運算式的 GUID。  
  
## <a name="syntax"></a>語法  
  
```  
  
      __uuidof (  
   expression   
)  
```  
  
## <a name="remarks"></a>備註  
 *運算式*可以是型別名稱、 指標、 參考或該類型的陣列，這些型別或這些類型的變數上的特製化樣板。 只要編譯器可以用它來尋找附加的 GUID，則引數有效。  
  
 這個內建特殊案例是當任一**0**或**NULL**提供做為引數。 在這種情況下，`__uuidof` 會傳回由零組成的 GUID。  
  
 使用這個關鍵字擷取附加至下列項目的 GUID：  
  
-   物件的[uuid](../cpp/uuid-cpp.md)擴充的屬性。  
  
-   使用建立的程式庫區[模組](../windows/module-cpp.md)屬性。  
  
> [!NOTE]
>  在偵錯組建，`__uuidof` 永遠動態地初始化物件 (在執行階段)。 在發行組建中，`__uuidof` 可以靜態地 (在編譯時期) 初始化物件。  
  
## <a name="example"></a>範例  
 下列程式碼 (以 ole32.lib 編譯) 會顯示以模組屬性所建立之程式庫區塊的 uuid：  
  
```  
// expre_uuidof.cpp  
// compile with: ole32.lib  
#include "stdio.h"  
#include "windows.h"  
  
[emitidl];  
[module(name="MyLib")];  
[export]  
struct stuff {  
   int i;  
};  
  
int main() {  
   LPOLESTR lpolestr;  
   StringFromCLSID(__uuidof(MyLib), &lpolestr);  
   wprintf_s(L"%s", lpolestr);  
   CoTaskMemFree(lpolestr);  
}  
```  
  
## <a name="comments"></a>註解  
 在範圍中不會再為程式庫名稱的情況下，您可以使用 __LIBID\_而不是`__uuidof`。 例如:   
  
```  
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [關鍵字](../cpp/keywords-cpp.md)