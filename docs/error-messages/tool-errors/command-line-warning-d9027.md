---
title: 命令列警告 D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 46ed5750bd1f315f20658ace9b83fac532fbbabb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196673"
---
# <a name="command-line-warning-d9027"></a>命令列警告 D9027

已忽略原始檔 '\<檔案名 > '

CL 已忽略輸入來源檔案。

此警告可能是由/Fo 選項與命令列上具有/c 選項的輸出檔案名之間的一個空格所造成。 例如：

```
cl /c /Fo output.obj input.c
```

因為在/Fo 和 `output.obj`之間有一個空格，所以 CL 會採用 `output.obj` 做為輸入檔的名稱。 若要修正此問題，請移除下列空間：

```
cl /c /Fooutput.obj input.c
```
