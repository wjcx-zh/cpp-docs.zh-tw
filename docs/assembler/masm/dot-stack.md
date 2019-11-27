---
title: .STACK
ms.date: 11/05/2019
f1_keywords:
- .STACK
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
ms.openlocfilehash: aabb2fc1267277aded4802fc8e1992f6a5c78ced
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397899"
---
# <a name="stack-32-bit-masm"></a>.堆疊（32位 MASM）

與搭配使用時[。MODEL](../../assembler/masm/dot-model.md)，定義堆疊區段（含有區段名稱**堆疊**）。 選擇性的*大小*會指定堆疊的位元組數目（預設值為1024）。 **。STACK**指示詞會自動關閉堆疊語句。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.STACK** ⟦*大小*⟧

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)
