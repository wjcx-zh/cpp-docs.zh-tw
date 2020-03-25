---
title: 資源編譯器嚴重錯誤 RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 9b6697dff0a445cc342f30d08bd79822b02df7b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172720"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>資源編譯器嚴重錯誤 RW1025

遠超出堆積記憶體

檢查可能佔用太多空間的記憶體常駐軟體。 使用 CHKDSK 程式來找出您有多少記憶體。

如果您要建立大型資源檔，請將資源腳本分割成兩個檔案。 建立兩個 .res 檔案之後，請使用 MS-DOS 命令列將它們聯結在一起：

```
copy first.res /b + second.res /b full.res
```
