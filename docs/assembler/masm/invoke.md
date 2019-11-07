---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 853bc9cd22d866357a4cd2d695beccc3efc20acf
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703970"
---
# <a name="invoke-32-bit-masm"></a>INVOKE （32位 MASM）

在*運算式*所指定的位址上呼叫程式，並根據語言類型的標準呼叫慣例，傳遞堆疊上或在暫存器中的引數。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> INVOKE*運算式*[[，*引數*]]

## <a name="remarks"></a>備註

傳遞至程式的每個引數都可以是運算式、暫存器組或位址運算式（前面加上 `ADDR`的運算式）。

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>