---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 94af498865151ff5c49fac9dbc03de65c4ecb934
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327599"
---
# <a name="local-masm"></a>LOCAL (MASM)

在巨集內的第一個指示詞**本機**定義巨集的每個執行個體是唯一的標籤。

## <a name="syntax"></a>語法

> 本機*localname* \[， *localname*]...
>
> 本機*標籤* \[ __\[__*計數*__]__ ] \[ __:__ *型別*] \[ __，__ *標籤* \[ __\[__*計數*__]__ ] \[*型別*]]...

## <a name="remarks"></a>備註

在程序定義中的第二個指示詞 (**PROC**)，**本機**建立存在的程序期間的堆疊式變數。 *標籤*可能是簡單的變數或陣列，其中包含*計數*項目。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>