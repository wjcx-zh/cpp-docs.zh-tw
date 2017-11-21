---
title: "__identifier (c + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs: C++
helpviewer_keywords: __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d9eca3bf99c0a798fd31dfa70e00769274a379b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)
可讓您使用 Visual c + + 關鍵字當做識別項。  
  
## <a name="all-platforms"></a>所有平台  
**語法**  
  
```  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
**備註**  
  
使用`__identifier`關鍵字不是關鍵字的識別項是允許的但強烈不建議使用的樣式。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 在下列範例中，類別命名為`template`C# 中建立並發佈成 DLL 的形式。 使用 Visual c + + 程式中`template`類別`__identifier`關鍵字隱藏事實，`template`是標準 c + + 關鍵字。  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **備註**  
  
 `__identifier`關鍵字是與有效**/clr**編譯器選項。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 在下列範例中，類別命名為`template`C# 中建立並發佈成 DLL 的形式。 使用 Visual c + + 程式中`template`類別`__identifier`關鍵字隱藏事實，`template`是標準 c + + 關鍵字。  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)   
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)