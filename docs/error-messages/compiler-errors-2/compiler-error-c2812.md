---
title: 編譯器錯誤 C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: cec92982646c64e6c5b669df328e4836d4f44df8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202092"
---
# <a name="compiler-error-c2812"></a>編譯器錯誤 C2812

> /clr： pure 和/clr： safe 不支援 \#匯入

## <a name="remarks"></a>備註

**/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

**/clr： pure**和 **/clr： safe**不支援[#import](../../preprocessor/hash-import-directive-cpp.md)指示詞，因為 `#import` 需要使用原生編譯器支援程式庫。

## <a name="example"></a>範例

下列範例會產生 C2812。

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```
