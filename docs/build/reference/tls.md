---
title: -TLS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78f485a783dbe8b5fe9a49ed3100754115bf50b8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714648"
---
# <a name="tls"></a>/TLS

顯示 IMAGE_TLS_DIRECTORY 結構從可執行檔。

## <a name="remarks"></a>備註

/ TLS 結構的欄位以及 TLS 回呼函式的位址，則會顯示 TLS。

如果程式不會使用執行緒區域儲存區，其映像不會包含 TLS 結構。  請參閱[執行緒](../../cpp/thread.md)如需詳細資訊。

IMAGE_TLS_DIRECTORY winnt.h 中定義。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](../../build/reference/dumpbin-options.md)