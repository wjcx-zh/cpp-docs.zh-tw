---
title: "覆寫規範 (C++ 元件擴充功能) | Microsoft Docs"
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
  - "覆寫規範, Visual C++"
  - "覆寫規範"
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 覆寫規範 (C++ 元件擴充功能)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「*覆寫規範*」\(Override Specifier\) 會修改繼承型別和繼承型別的成員在衍生型別中的行為方式。  
  
## 所有執行階段  
 **備註**  
  
 如需覆寫規範的詳細資訊，請參閱：  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [new \(vtable 中的新位置\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   [覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)  
  
 `abstract` 和 `sealed` 也適用於型別宣告，而它們不會在其中做為覆寫規範。  
  
 如需明確覆寫基底類別函式的詳細資訊，請參閱[明確覆寫](../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## Windows 執行階段  
 \(這個語言功能沒有只適用於 Windows 執行階段的備註。\)  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 \(這個語言功能沒有只適用於 Common Language Runtime 的備註。\)  
  
### 需求  
 編譯器選項：**\/clr**  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)