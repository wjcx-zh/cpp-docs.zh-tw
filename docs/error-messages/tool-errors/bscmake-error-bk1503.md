---
title: BSCMAKE 錯誤 BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: e0f05b3979024cb053394c51fa9337197b5de7bf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197856"
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE 錯誤 BK1503

無法寫入檔案 ' filename ' [： reason]

BSCMAKE 將編譯期間產生的 .sbr 檔案結合成一個瀏覽器資料庫。 如果產生的瀏覽器資料庫超過 64 MB，或輸入（.sbr）檔案數目超過4092，則會發出此錯誤。

如果問題是由超過4092的 .sbr 檔案所造成，您就必須減少輸入檔的數目。 從 Visual Studio 中，您可以透過[/fr](../../build/reference/fr-fr-create-dot-sbr-file.md)整個專案來完成這項作業，然後依檔案逐一檢查檔案。

如果問題是由大於64MB 的 .bsc 檔案所造成，則減少 .sbr 檔案的數目做為輸入，將會減少產生的 .bsc 檔案大小。 此外，流覽資訊的數量可能會透過使用/Em （排除宏展開的符號）、/El （排除區域變數）和/Es （排除系統檔案）而降低。

## <a name="see-also"></a>另請參閱

[BSCMAKE 選項](../../build/reference/bscmake-options.md)
