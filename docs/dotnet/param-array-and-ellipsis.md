---
title: Param 陣列和省略 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 20d13f327abe3e864007c4941af2ce9fd03ea05d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="param-array-and-ellipsis"></a>Param 陣列和省略
Param 陣列來解析多載函式呼叫的優先順序已經從 Managed Extensions for c + + Visual c + +。  
  
 在受管理的擴充功能和新語法中，沒有明確支援 C# 和 Visual Basic 支援 param 陣列。 相反地，其中一個旗標與屬性，一般陣列，如下所示：  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 雖然這兩個相同，`ParamArray`屬性加上標記 （C#） 或其他 CLR 語言以進行每次叫用的項目數目可變陣列。 行為之間受管理的擴充功能和新語法的程式中的變更是在哪一個執行個體宣告省略符號設定的多載函式的解析與第二個宣告`ParamArray`屬性，如下列範例所提供Artur Laksberg。  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 在 Managed Extensions，省略符號是優先於這很合理，因為屬性不是語言的正式層面的屬性。 不過，在新語法中，param 陣列現在支援語言，在直接，而且它會優先於省略符號因為更強型別。 因此，在 Managed Extensions，呼叫  
  
```  
fx( 1, 2 );  
```  
  
 解析成`fx(...)`而在新語法中，它會解析為`ParamArray`執行個體。 保有您程式的行為取決於省略執行個體的引動過程高於`ParamArray`，您必須修改的簽章或呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)