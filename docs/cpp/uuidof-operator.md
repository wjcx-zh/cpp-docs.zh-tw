---
title: "__uuidof 運算子 | Microsoft Docs"
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
  - "__LIBID_"
  - "__LIBID_cpp"
  - "__uuidof"
  - "__uuidof_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__LIBID_ 關鍵字 [C++]"
  - "__uuidof 關鍵字 [C++]"
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __uuidof 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 擷取 GUID 附加至運算式。  
  
## 語法  
  
```  
  
      __uuidof (  
   expression   
)  
```  
  
## 備註  
 *運算式* 可以是型別名稱、指標、參考或型別特製化的參考、範本或這些型別的變數。  只要編譯器可以用它來尋找附加的 GUID，則引數有效。  
  
 這個內建特殊案例是當 **0** 或 **NULL** 會提供做為引數。  在這種情況下， `__uuidof` 會傳回由零組成的 GUID 。  
  
 使用這個關鍵字擷取 GUID 附加至：  
  
-   由 [uuid](../cpp/uuid-cpp.md) 擴充屬性的物件。  
  
-   程式庫區塊會為具有 [模組](../windows/module-cpp.md) 屬性。  
  
> [!NOTE]
>  在偵錯組建， `__uuidof` 永遠動態地初始化物件 \(在執行階段\)。  在發行的組建中， `__uuidof` 靜態地 \(在編譯時期\) 初始化物件。  
  
## 範例  
 下列程式碼 \(以 ole32.lib 編譯\) 會顯示程式庫區塊中的 uuid 建立模組屬性:  
  
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
  
## 註解  
 萬一程式庫名稱不在範圍內，您可以使用 \_\_LIBID\_ 而不是 `__uuidof`。  例如：  
  
```  
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **END Microsoft 專有**  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)