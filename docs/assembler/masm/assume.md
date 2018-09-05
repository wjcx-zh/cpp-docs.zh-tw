---
title: 假設 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ASSUME
dev_langs:
- C++
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0e43548292d2ffecbebdaead6aa12d6dacc352
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693804"
---
# <a name="assume"></a>ASSUME

啟用檢查暫存器值時發生錯誤。

## <a name="syntax"></a>語法

> ASSUME *segregister*:*名稱*[[， *segregister*:*名稱*]]...<br/>
> ASSUME *dataregister*:*型別*[[， *dataregister*:*類型*]]...<br/>
> ASSUME*註冊*： 錯誤 [[，*註冊*： 錯誤]]...<br/>
> 假設 [[*註冊*:]] 執行任何動作 [[，*註冊*： 執行任何動作]]...


## <a name="remarks"></a>備註

之後`ASSUME`會放入效果，組合器會監看的指定暫存器的值變更。 **錯誤**如果崞紵呇樾會產生錯誤。 **NOTHING**移除註冊錯誤檢查。 您可以結合不同類型的一個陳述式中的假設。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>