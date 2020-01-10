---
title: ML 嚴重錯誤 A1010
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: b3141f8819a33281c70e34bd7772d4475886e557
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312582"
---
# <a name="ml-fatal-error-a1010"></a>ML 嚴重錯誤 A1010

**不相符的區塊嵌套：**

區塊開頭沒有相符的結尾，或區塊結尾沒有相符的開始。 可能牽涉到下列其中一項：

- 高階指示詞，例如[。如果](dot-if.md)為，則為[。重複](dot-repeat.md)、或[。WHILE](dot-while.md)。

- 條件式元件指示詞，例如[IF](if-masm.md)、 [REPEAT](repeat.md)或**WHILE**。

- 結構或等位定義。

- 程序定義。

- 區段定義。

- [POPCONTEXT](popcontext.md)指示詞。

- 條件式元件指示詞，例如[ELSE](else-masm.md)、 [ELSEIF](elseif-masm.md)或**ENDIF** ，但不含符合的[IF](if-masm.md)。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](ml-error-messages.md)
