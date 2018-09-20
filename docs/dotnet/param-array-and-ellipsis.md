---
title: Param 陣列和省略 |Microsoft Docs
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
ms.openlocfilehash: 2caf6415fdbceb506b736e209c6e7e384b567c5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384373"
---
# <a name="param-array-and-ellipsis"></a>Param 陣列和省略

Param 陣列，用於解析多載函式呼叫的優先順序已從 Managed Extensions for c + + Visual c + +。

在受管理的擴充功能和新語法中，沒有明確支援 C# 和 Visual Basic 支援的參數陣列。 相反地，其中一個旗標具有屬性 (attribute) 的一般陣列，如下所示：

```
void Trace1( String* format, [ParamArray]Object* args[] );
void Trace2( String* format, Object* args[] );
```

雖然這兩個相同，`ParamArray`屬性加上標記，適用於 C# 或其他 CLR 語言為陣列的每次叫用的項目數量。 Managed Extensions 和新的語法之間的程式中的行為變更會解析設定中的一個執行個體宣告省略符號多載函式，並在第二個宣告`ParamArray`屬性，如下列所提供的範例所示Artur Laksberg。

```
int fx(...); // 1
int fx( [ParamArray] Int32[] ); // 2
```

管理擴充功能中的省略符號是優先於很合理，因為屬性不是語言的正式層面的屬性。 不過，在新語法中，param 陣列現在支援直接在語言中，而且它會指定優先順序的省略符號，因為它更強型別。 因此，在受管理的擴充功能，呼叫

```
fx( 1, 2 );
```

會解析成`fx(...)`而在新語法中，它會解析為`ParamArray`執行個體。 保有您程式的行為取決於引動過程的省略符號 」 執行個體的程序的`ParamArray`，您必須修改簽章或呼叫。

## <a name="see-also"></a>另請參閱

[一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)