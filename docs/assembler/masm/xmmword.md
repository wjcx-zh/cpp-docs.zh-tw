---
title: XMMWORD
ms.date: 08/30/2018
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: c7783049a143b19295a67cd3e9e40afeab3c814f
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74392797"
---
# <a name="xmmword"></a>XMMWORD

用於具有 MMX 和 SSE （XMM）指令的128位多媒體運算元。

## <a name="syntax"></a>語法

> **XMMWORD**

## <a name="remarks"></a>備註

**XMMWORD**的目的是要代表與[__m128](../../cpp/m128.md)相同的類型。

## <a name="example"></a>範例

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```
