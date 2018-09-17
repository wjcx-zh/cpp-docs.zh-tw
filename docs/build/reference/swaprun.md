---
title: -SWAPRUN |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /swaprun
dev_langs:
- C++
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a93b854dba2855fa68bb3be163cecdcd3570df0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723092"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>備註

此選項可編輯影像，告知作業系統映像複製到交換檔，並從該處執行它。 使用此選項位於卸除式媒體或網路上的映像。

您可以新增或移除 NET 或 CD 限定詞：

- NET 指出映像位於網路上。

- CD 指出映像所在的 CD-ROM 或類似的卸除式媒體上。

- 使用 ！ NET 和 ！若要反轉 NET 和 CD 的效果的 CD。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](../../build/reference/editbin-options.md)