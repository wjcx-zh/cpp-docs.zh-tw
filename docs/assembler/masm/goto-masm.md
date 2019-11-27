---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 424ff295fe37e7c5ff02897a01b99a7c75876f85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397488"
---
# <a name="goto-masm"></a>GOTO (MASM)

將元件傳輸到標記為 **：** _macrolabel_的行。

## <a name="syntax"></a>語法

> **GOTO** *macrolabel*

## <a name="remarks"></a>備註

只有在[宏](macro.md)、 [FOR](for-masm.md)、 [FORC](forc.md)、 [REPEAT](repeat.md)和[WHILE](while-masm.md)區塊中才允許**GOTO** 。 *Macrolabel*目標必須是行上的唯一指示詞，且前面必須加上前置冒號。

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)
