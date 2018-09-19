---
title: 連結器工具警告 LNK4071 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4071
dev_langs:
- C++
helpviewer_keywords:
- LNK4071
ms.assetid: 803f8c34-8219-4f55-a4ae-7133ceff2ba3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11247c823a93604359b4cab6995b694bcf5a2f3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064662"
---
# <a name="linker-tools-warning-lnk4071"></a>連結器工具警告 LNK4071

無法以累加方式連結於在後續的連結

連結中找到多個定義一或多個符號，但[/force](../../build/reference/force-force-file-output.md)或 **/force: multiple 都會**用來建立輸出檔，不論錯誤為何。 刪除連結的累加狀態 (.ilk) 檔案。