---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c3a04f68b7fd17b2b6459c219a98fd99ec2d62d4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397247"
---
# <a name="local-masm"></a>LOCAL (MASM)

在宏內的第一個指示詞中， **LOCAL**會定義每個宏實例特有的標籤。

## <a name="syntax"></a>語法

> **本機** *localname* ⟦， *localname* .。。⟧
>
> **本機***標籤*⟦ __\[__ *計數* __]__ ⟧ __⟦：__ *類型*⟧⟦ __，__ *標籤*⟦ __\[__ *計數* __]__ ⟧⟦*類型*⟧ .。。⟧

## <a name="remarks"></a>備註

在第二個指示詞中，在程序定義（**PROC**）內， **LOCAL**會建立在程式期間存在的堆疊型變數。 *標籤*可以是簡單變數或包含*計數*元素的陣列。

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)
