---
title: "靜態 Const 整數連結不再是常值 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常數, 宣告"
  - "整數常數運算式"
  - "literal 屬性 [C++]"
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 靜態 Const 整數連結不再是常值
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，類別的常數成員宣告已變更。  
  
 雖然還是支援 `static const` 整數成員，但它們的連結屬性 \(Attribute\) 已有所變更。  舊的連結屬性現在包含在常值 \(Literal\) 整數成員中。  例如，請考慮下列 Managed Extensions 類別：  
  
```  
public __gc class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 這會為欄位產生下列基礎 CIL 屬性 \(請注意常值屬性\)：  
  
```  
.field public static literal int32   
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 仍在新語法底下編譯時：  
  
```  
public ref class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 它再也不會發出常值屬性，因此 CLR 執行階段不會將它視為常數：  
  
```  
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 若要擁有相同的語言間常值屬性，可以將宣告變更為剛支援的 `literal` 資料成員，如下所示，  
  
```  
public ref class Constants {  
public:  
   literal int LOG_DEBUG = 4;  
};  
```  
  
## 請參閱  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [literal](../windows/literal-cpp-component-extensions.md)