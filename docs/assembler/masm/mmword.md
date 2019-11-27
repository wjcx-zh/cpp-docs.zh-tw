---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: d4378c1435df09f249fe7f55dabd4bd0f43f6100
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397167"
---
# <a name="mmword"></a>MMWORD

用於具有 MMX 和 SSE （XMM）指令的64位多媒體運算元。

## <a name="syntax"></a>語法

> **MMWORD**

## <a name="remarks"></a>備註

**MMWORD**是一種類型。  在將**MMWORD**新增至 MASM 之前，您可以透過下列方式來達成對等的功能：

```asm
    mov mm0, qword ptr [ebx]
```

雖然這兩個指示都適用于64位運算元，但**QWORD**是64位不帶正負號的整數的類型，而**MMWORD**是64位多媒體值的類型。

**MMWORD**的目的是要代表與[__m64](../../cpp/m64.md)相同的類型。

## <a name="example"></a>範例

```asm
    movq     mm0, mmword ptr [ebx]
```
