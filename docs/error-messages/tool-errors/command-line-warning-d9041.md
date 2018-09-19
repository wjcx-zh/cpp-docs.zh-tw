---
title: 命令列警告 D9041 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9041
dev_langs:
- C++
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70bf82cfdca787898a02fb52926981bfd1a1b3e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033377"
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