---
title: Varargs |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8305eaddf87a2e67b797bedff1944dbcbbbdbd41
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713644"
---
# <a name="varargs"></a>Varargs

如果參數傳遞透過 varargs （比方說，省略引數），基本上是正常的參數傳遞適用於包括溢出，第五個和後續引數。 它負責一次被呼叫端的傾印的引數，取得其位址。 對於只有浮點數值，整數和浮點暫存器會包含浮點值萬一被呼叫端需要整數暫存器值。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)