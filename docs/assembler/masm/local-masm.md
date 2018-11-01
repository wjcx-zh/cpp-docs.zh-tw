---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c8ea49b9862159a5a56bfb3d2c3cd0c1f4cd7413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596868"
---
# <a name="local-masm"></a>LOCAL (MASM)

在巨集內的第一個指示詞**本機**定義巨集的每個執行個體是唯一的標籤。

## <a name="syntax"></a>語法

> 本機*localname* [[， *localname*]]...

> 本機*標籤*[[[*計數*]]] [[:*型別*]] [[，*標籤*[[[*計數*]]] [[*型別*]]]]...

## <a name="remarks"></a>備註

在程序定義中的第二個指示詞 (**PROC**)，**本機**建立存在的程序期間的堆疊式變數。 *標籤*可能是簡單的變數或陣列，其中包含*計數*項目。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>