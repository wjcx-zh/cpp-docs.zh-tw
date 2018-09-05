---
title: 本機 (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8105bc8168ce28d468a1378c5cf7889907a7c9f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685059"
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