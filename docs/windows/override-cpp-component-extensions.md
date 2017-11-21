---
title: "覆寫 （c + + 元件擴充功能） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c16b79d50ad0494956ee27f0928daabfefdacaed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="override--c-component-extensions"></a>override (C++ 元件擴充功能)
`override` 即時線上關鍵字表示，類型成員會覆寫基底類別或基底介面成員。  
  
## <a name="remarks"></a>備註  
 `override`關鍵字對原生目標 （預設編譯器選項），在編譯時是有效 Windows 執行階段為目標 (**/ZW**編譯器選項)，或通用語言執行階段為目標 (**/clr**編譯器選項）。  
  
 如需覆寫規範的詳細資訊，請參閱[覆寫規範](../cpp/override-specifier.md)和[覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
 如需內容相關性關鍵字的詳細資訊，請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## <a name="examples"></a>範例  
 **範例**  
  
 下列程式碼範例顯示`override`也可用在原生編譯中。  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **範例**  
  
 下列程式碼範例顯示`override`可用在 Windows 執行階段編譯中。  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Requirements**  
  
 編譯器選項： **/ZW**  
  
 **範例**  
  
 下列程式碼範例顯示`override`可以在通用語言執行階段編譯中使用。  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Requirements**  
  
 編譯器選項： **/clr**  
  
## <a name="see-also"></a>另請參閱  
 [覆寫規範](../cpp/override-specifier.md)   
 [覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)