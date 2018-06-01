---
title: 編譯器錯誤 C3389 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b540f87458c75ddf7d57626b6251248652b96213
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704301"
---
# <a name="compiler-error-c3389"></a>編譯器錯誤 C3389

> __declspec (*關鍵字*) 不能以 /clr: pure 或 /clr: safe

## <a name="remarks"></a>備註

**/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

A [__declspec](../../cpp/declspec.md)修飾詞表示每個處理序狀態。  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)表示每個[appdomain](../../cpp/appdomain.md)狀態。  因此，宣告的變數`keyword` **__declspec**修飾詞和編譯 **/clr: pure**不允許。

## <a name="example"></a>範例

下列範例會產生 C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```