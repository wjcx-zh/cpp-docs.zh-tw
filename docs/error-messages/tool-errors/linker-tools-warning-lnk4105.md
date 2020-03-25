---
title: 連結器工具警告 LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 655a6dfde77984cd0c941ec0d8abb0c4d099c80f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183289"
---
# <a name="linker-tools-warning-lnk4105"></a>連結器工具警告 LNK4105

未使用選項 ' option ' 指定引數;忽略選項

只有在設定[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項時，才會發生此警告。 如果未使用此選項指定目錄，則連結器會忽略選項，並產生此警告訊息。

如果您不需要覆寫現有的環境程式庫設定，請從連結器命令列中移除/LIBPATH 選項。 如果您想要使用程式庫的替代搜尋路徑，請在/LIBPATH 選項之後指定替代路徑。

## <a name="example"></a>範例

```
link /libpath:c:\filepath\lib bar.obj
```

會指示連結器在搜尋預設位置之前，先在 `c:\filepath\lib` 中搜尋所需的程式庫。
