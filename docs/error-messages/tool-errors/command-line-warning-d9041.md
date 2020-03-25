---
title: 命令列警告 D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 7c685a1ca3195ad4ab52bab8b5d32b1a51534b24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196571"
---
# <a name="command-line-warning-d9041"></a>命令列警告 D9041

'/option ' 的值 ' value ' 無效;假設「值」;指定此警告時，將 '/analyze ' 新增至命令列選項

程式碼分析警告編號已新增至 **/wd**、 **/we**、 **/wo**或 **/wl**命令列選項，但未同時指定 **/analyze**命令列選項。 若要補救此錯誤，請新增 **/analyze**命令列選項，或從適當的 **/w**命令列選項中移除不正確警告編號。

## <a name="example"></a>範例

下列命令列範例會產生警告 D9041：

```
cl /EHsc /LD /wd6001 filename.cpp
```

若要修正此警告，請新增 **/analyze**命令列選項。 如果您的編譯器版本不支援 **/analyze** ，請從 **/wd**選項移除不正確警告編號。

## <a name="see-also"></a>另請參閱

[命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC 編譯器選項](../../build/reference/compiler-options.md)
