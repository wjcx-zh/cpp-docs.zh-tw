---
title: 靜態 Const 整數連結不再是常值 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- literal attribute [C++]
- constants, declaring
- integral constant expressions
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cc3f72080c08807026c6458979ac0ba561e298df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>靜態 Const 整數連結不再是常值
宣告常數成員的類別已從 Managed Extensions for c + + Visual c + +。  
  
 雖然`static const`仍然支援整數類資料成員、 其連結屬性已變更。 其先前的連結屬性現在會執行的常值的整數類資料成員中。 例如，請考慮下列管理延伸模組類別：  
  
```  
public __gc class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 這會產生下列基礎的 CIL 屬性欄位 （請注意常值的屬性）：  
  
```  
.field public static literal int32   
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 雖然這仍會在新語法中編譯：  
  
```  
public ref class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 它不會發出常值的屬性，並因此不視為常數 CLR 執行階段：  
  
```  
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 應該有相同的語言間常值的屬性，才能變更宣告以新支援`literal`，如下所示，資料成員  
  
```  
public ref class Constants {  
public:  
   literal int LOG_DEBUG = 4;  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [在類別或介面中的成員宣告 (C + + /CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [常值](../windows/literal-cpp-component-extensions.md)