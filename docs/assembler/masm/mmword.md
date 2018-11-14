---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: e4ebaa9d47a569bc9cf7d843d3ddb54ca5d713a0
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328223"
---
# <a name="mmword"></a>MMWORD

用於 MMX 和 SSE (XMM) 指示的 64 位元多媒體運算元。

## <a name="syntax"></a>語法

> MMWORD

## <a name="remarks"></a>備註

`MMWORD` 是一種。  之前加入 MASM MMWORD，對等的功能可能已享有的：

```asm
    mov mm0, qword ptr [ebx]
```

雖然這兩個指示作用於 64 位元運算元`QWORD`是 64 位元不帶正負號整數的類型和`MMWORD`是 64 位元多媒體值的類型。

`MMWORD` 用來表示相同的型別[__m64](../../cpp/m64.md)。

## <a name="example"></a>範例

```asm
    movq     mm0, mmword ptr [ebx]
```