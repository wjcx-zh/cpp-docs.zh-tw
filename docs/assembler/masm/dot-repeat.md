---
title: .重複 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8856ed0e1d86277a413baac2c56e5c5ca2ea9ff0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687948"
---
# <a name="repeat"></a>.REPEAT

會產生重複的區塊執行的程式碼*陳述式*直到`condition`變成 true。 [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，而成為，則為 true，當 CX 是零，可能會替換為[。直到](../../assembler/masm/dot-until.md)。 `condition`是選擇性的 with **。UNTILCXZ**。

## <a name="syntax"></a>語法

> .REPEAT<br/>
> 陳述式<br/>
> .UNTIL 條件

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>