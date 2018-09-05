---
title: GOTO (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0be678e2d39389cbc551c386c1890f799124b5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43694013"
---
# <a name="goto-masm"></a>GOTO (MASM)

將組件傳送至標記的一行 **:**_macrolabel_。

## <a name="syntax"></a>語法

> **GOTO** *macrolabel*

## <a name="remarks"></a>備註

**GOTO**允許只在[巨集](macro.md)， [FOR](for-masm.md)， [FORC](forc.md)，[重複](repeat.md)，和[時](while-masm.md)區塊。 *Macrolabel*目標必須是該行的唯一指示詞，而且必須加上前置的冒號。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
