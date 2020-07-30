---
title: 命令列警告 D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: e685e9bd0ffb58065f20f466131f8894baaf359f
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389723"
---
# <a name="command-line-warning-d9041"></a>命令列警告 D9041

> 不正確值 '*選項-值*' 代表 '/*選項名稱*';假設為 '*假設值*';指定此警告時，將 '/analyze ' 新增至命令列選項

程式碼分析警告編號已加入 **`/wd`** 、 **`/we`** 、 **`/wo`** 或 **`/wl`** 命令列選項，但未同時指定 **`/analyze`** 命令列選項。 若要解決這個錯誤，請新增 **`/analyze`** 命令列選項，或從適當的命令列選項中移除不正確警告編號 **`/w`** 。

## <a name="example"></a>範例

下列命令列範例會產生警告 D9041：

```cmd
cl /EHsc /LD /wd6001 filename.cpp
```

若要修正此警告，請新增 **`/analyze`** 命令列選項。 如果 **`/analyze`** 您的編譯器版本不支援，請從選項中移除不正確警告編號 **`/wd`** 。

## <a name="see-also"></a>另請參閱

[命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC 編譯器選項](../../build/reference/compiler-options.md)
