---
title: 嚴重錯誤 C1190
ms.date: 11/04/2016
f1_keywords:
- C1190
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
ms.openlocfilehash: 8bd0332770dd0771ac7a02574185a506cf6fd416
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228900"
---
# <a name="fatal-error-c1190"></a>嚴重錯誤 C1190

Managed 目標程式碼需要 '/clr' 選項

您使用 CLR 建構，但未指定 **/clr**。

如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md)。

下列範例會產生 C1190：

```
// C1190.cpp
// compile with: /c
__gc class A {};   // C1190
ref class A {};
```