---
title: BSCMAKE 命令列
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: 7724069a401aadcdb2e3e8487dc85273dac357fc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818644"
---
# <a name="bscmake-command-line"></a>BSCMAKE 命令列

若要執行 BSCMAKE，使用下列命令列語法：

```
BSCMAKE [options] sbrfiles
```

選項僅可出現在`options`命令列上的欄位。

*Sbrfiles*欄位會指定一或多個編譯器或組譯工具所建立的.sbr 檔案。 使用空格或定位字元分隔.sbr 檔案的名稱。 您必須指定擴充功能;沒有預設值。 您可以指定的路徑與檔名，而且您可以使用作業系統萬用字元 (\*和？)。

在累加建置，您可以指定新的.sbr 檔案未包含的原始的組建。 如果您想要保留在瀏覽資訊檔中的所有成果，您必須指定所有.sbr 檔 （包括已截斷的檔案），最初用來建立.bsc 檔案。 如果您省略的.sbr 檔案時，會移除該檔案的貢獻，以瀏覽資訊檔。

未指定完整的組建的已截斷的.sbr 檔案。 完整的建置需要從所有指定的.sbr 檔案。 執行完整建置之前，請重新編譯專案，並建立新的.sbr 檔，針對每個空的檔案。

下列命令會執行 BSCMAKE 來建置呼叫 MAIN.bsc 從三個.sbr 檔案檔：

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

如需相關資訊，請參閱[BSCMAKE 命令檔](bscmake-command-file-response-file.md)並[BSCMAKE 選項](bscmake-options.md)。

## <a name="see-also"></a>另請參閱

[BSCMAKE 參考](bscmake-reference.md)
