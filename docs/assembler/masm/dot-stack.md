---
title: .STACK
ms.date: 11/05/2019
f1_keywords:
- .STACK
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
ms.openlocfilehash: 78c089c771e8e5a8c82905578ec2377246a44a0e
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703526"
---
# <a name="stack-32-bit-masm"></a>.堆疊（32位 MASM）

與搭配使用時[。MODEL](../../assembler/masm/dot-model.md)，定義堆疊區段（含有區段名稱堆疊）。 選擇性的 `size` 會指定堆疊的位元組數目（預設值1024）。 `.STACK` 指示詞會自動關閉堆疊語句。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> .堆疊 [[大小]]

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>