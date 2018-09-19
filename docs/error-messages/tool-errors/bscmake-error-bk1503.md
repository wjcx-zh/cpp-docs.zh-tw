---
title: BSCMAKE 錯誤 BK1503 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16bf228804cb24f4fe7a2428dc581116d4cec91d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064659"
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE 錯誤 BK1503

無法寫入檔案 'filename' [: 原因]

BSCMAKE 結合成單一的瀏覽器資料庫在編譯期間產生的.sbr 檔案。 如果產生的瀏覽器資料庫超過 64 MB，或是輸入 (.sbr) 檔案數目超過 4092，就會發出此錯誤。

如果問題因為多個 4092.sbr 檔，您必須減少輸入的檔案數目。 從 Visual Studio 中，這可透過[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)您整個專案，然後重新檢查檔案的方式為基礎。

如果問題因為.bsc 檔案大於 64 MB，減少做為輸入的.sbr 檔數目會減少產生的.bsc 檔的大小。 此外，瀏覽資訊的數量可能會減少 / e m （排除巨集擴充符號）、 /El （排除區域變數） 和 /Es （排除系統檔案）。

## <a name="see-also"></a>另請參閱

[BSCMAKE 選項](../../build/reference/bscmake-options.md)