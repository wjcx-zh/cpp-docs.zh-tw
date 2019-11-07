---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 4bf8f0c41e9ce3e296cf201efd4fd9be2033cbdb
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73702469"
---
# <a name="assume-32-bit-masm"></a>假設（32位 MASM）

啟用註冊值的錯誤檢查。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> 假設*segregister*：*name* [[， *segregister*：*name*]] 。<br/>
> 假設*dataregister*：*type* [[， *dataregister*：*type*]] 。<br/>
> 假設*register*： ERROR [[， *register*： ERROR]] 。<br/>
> 假設 [[*register*：]] 沒有 [[， *register*：無]] 。

## <a name="remarks"></a>備註

在 `ASSUME` 生效後，組合器會監看給定暫存器值的變更。 如果使用了暫存器，**錯誤**就會產生錯誤。 **任何內容都**不會移除註冊錯誤檢查。 您可以在一個語句中結合不同類型的假設。

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>