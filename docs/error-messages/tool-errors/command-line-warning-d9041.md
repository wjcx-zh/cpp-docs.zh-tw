---
title: 命令列警告 D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 79bdafcd4ed6af061b9c0ee27aae6eed6bc981a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513915"
---
# <a name="command-line-warning-d9041"></a>命令列警告 D9041

無效的值 'value' 的 '/option';假設 'value';加入 '/analyze' 命令列選項時指定這項警告

程式碼分析警告數字相加 **/wd**， **/we**， **/wo**，或 **/wl**命令列選項，但沒有同時指定 **/analyze**命令列選項。 若要解決這個錯誤，請新增 **/analyze**命令列選項，或移除無效的警告編號，從適當 **/w**命令列選項。

## <a name="example"></a>範例

下列的命令列範例會產生警告 D9041:

```
cl /EHsc /LD /wd6001 filename.cpp
```

若要修正此警告，新增 **/analyze**命令列選項。 如果 **/analyze**不是支援您版本的編譯器，移除無效的警告編號，從 **/wd**選項。

## <a name="see-also"></a>另請參閱

[命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)