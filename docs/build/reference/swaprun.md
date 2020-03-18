---
title: /SWAPRUN
ms.date: 11/04/2016
f1_keywords:
- /swaprun_editbin
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
ms.openlocfilehash: 83aa2cdb445ed1ac6bac5b1237f90a116986b0a9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438852"
---
# <a name="swaprun"></a>/SWAPRUN

```
/SWAPRUN:{[!]NET|[!]CD}
```

## <a name="remarks"></a>備註

此選項會編輯影像，告知作業系統將映射複製到交換檔，然後從該處執行。 如果是位於網路或卸載式媒體上的映射，請使用此選項。

您可以新增或移除 NET 或 CD 限定詞：

- NET 指出映射位於網路上。

- CD 表示影像位於 CD-ROM 或類似的卸載式媒體上。

- 使用！ NET 和！CD 來反轉 NET 和 CD 的效果。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)
