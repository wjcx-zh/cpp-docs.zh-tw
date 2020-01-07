---
title: 編譯器錯誤 C2449
ms.date: 11/04/2016
f1_keywords:
- C2449
helpviewer_keywords:
- C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
ms.openlocfilehash: 6fd62813fdf3b50c0e329fc423e100d55a36ae12
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299019"
---
# <a name="compiler-error-c2449"></a>編譯器錯誤 C2449

在檔案範圍找到 ' {' （遺漏函式標頭？）

檔案範圍內會出現一個左括弧。

這個錯誤可能是函式標頭與函式定義的左大括弧之間的分號所造成。

下列範例會產生 C2499：

```c
// C2449.c
// compile with: /c
void __stdcall func(void) {}   // OK
void __stdcall func(void);  // extra semicolon on this line
{                         // C2449 detected here
```
