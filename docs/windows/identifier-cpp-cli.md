---
title: __identifier (c + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14b68f573452d9ab8894027fd4d83c0b89f2ddf1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018357"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)
可讓您使用 Visual c + + 關鍵字當做識別項。  
  
## <a name="all-platforms"></a>所有平台  
### <a name="syntax"></a>語法  
  
```cpp  
__identifier(  
Visual_C++_keyword  
)  
```  
  
### <a name="remarks"></a>備註  
  
利用 **__identifier**關鍵字的識別項不是關鍵字是允許的但強烈不建議的樣式。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
  
### <a name="requirements"></a>需求  
 編譯器選項：`/ZW`  
  
### <a name="examples"></a>範例  
 **範例**  
  
 在下列範例中，具名的類別**範本**是在 C# 中建立和散發的 DLL。 使用的 Visual c + + 程式中**範本**類別 **_try**關鍵字會隱藏的事實，**範本**是標準的 c + + 關鍵字。  
  
```cs  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```cpp  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
### <a name="remarks"></a>備註  
  
 **__Identifier**關鍵字是適用於`/clr`編譯器選項。  
  
### <a name="requirements"></a>需求  
 編譯器選項：`/clr`  
  
### <a name="examples"></a>範例  
  
 在下列範例中，具名的類別**範本**是在 C# 中建立和散發的 DLL。 使用的 Visual c + + 程式中**範本**類別 **_try**關鍵字會隱藏的事實，**範本**是標準的 c + + 關鍵字。  
  
```cs  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```cpp  
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