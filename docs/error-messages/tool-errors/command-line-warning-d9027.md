---
title: 命令列警告 D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: f89e7416efe7a0069ee2dae8df921933bbe76bcf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482598"
---
# <a name="command-line-warning-d9027"></a>命令列警告 D9027

原始程式檔 '\<檔案名稱 >' 已忽略

CL.exe 略過輸入的來源檔案。

這個警告可能因 /Fo 選項和 /c 選項的命令列上的輸出檔案名稱之間的空格。 例如: 

```
cl /c /Fo output.obj input.c
```

因為 /Fo 之間的空間和`output.obj`，CL.exe 採用`output.obj`做為輸入檔案的名稱。 若要修正此問題，請將空格移除：

```
cl /c /Fooutput.obj input.c
```