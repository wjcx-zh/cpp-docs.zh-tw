---
title: .CODE | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff2d66cfc79e84c8c4c7cf92e117c9ac8c84a555
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682483"
---
# <a name="code"></a>.CODE

當搭配[。模型](../../assembler/masm/dot-model.md)，表示程式碼片段的開頭。

## <a name="syntax"></a>語法

> .程式碼 [[name]]

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`name`|指定的程式碼片段名稱的選擇性參數。 預設名稱是很小，很小，壓縮和一般 _TEXT[模型](../../assembler/masm/dot-model.md)。 預設名稱是*modulename*_TEXT 其他模型。|

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
[.DATA](../../assembler/masm/dot-data.md)<br/>