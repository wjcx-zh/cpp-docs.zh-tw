---
title: XMMWORD
ms.date: 08/30/2018
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 59d1ba71260ed08b761c332e887cf27517762303
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326338"
---
# <a name="xmmword"></a>XMMWORD

用於 MMX 和 SSE (XMM) 指示的 128 位元多媒體運算元。

## <a name="syntax"></a>語法

> XMMWORD

## <a name="remarks"></a>備註

`XMMWORD` 用來表示相同的型別[__m128](../../cpp/m128.md)。

## <a name="example"></a>範例

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```