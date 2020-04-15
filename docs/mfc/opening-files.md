---
title: 開啟檔案
ms.date: 11/04/2016
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
ms.openlocfilehash: 6119bf922b05c30a14d8421800e3931c4a038779
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375953"
---
# <a name="opening-files"></a>開啟檔案

在 MFC 中，最常見的開啟檔案方式是一個兩階段的程序。

#### <a name="to-open-a-file"></a>開啟檔案

1. 建立檔案物件，而不指定路徑或使用權限旗標。

   通常通過在堆疊幀上聲明[CFile](../mfc/reference/cfile-class.md)變數來創建檔物件。

1. 呼叫檔案物件的[Open](../mfc/reference/cfile-class.md#open)成員函數,提供路徑和許可權標誌。

   如果已成功開啟檔案，`Open` 會傳回非零值，如果無法開啟指定的檔案則會傳回 0。 `Open` 成員函式的原型如下：

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   開啟旗標指定您要為檔案指定的使用權限，例如唯讀。 可能的旗標值會在 `CFile` 類別中定義為列舉常數，使其符合 "`CFile::`" 的格式，如 `CFile::modeRead`。 如果您要建立檔案，請使用 `CFile::modeCreate` 旗標。

下列範例顯示如何建立具有讀取/寫入權限的新檔案 (取代任何具有相同路徑的舊檔案)：

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> 這個範例會建立並開啟檔案。 如果發生問題，則 `Open` 可能會在它的最後一個參數中傳回 `CFileException` 物件，如下所示。 TRACE 宏同時列印檔名和指示失敗原因的代碼。 如果需要更詳細的錯誤報告，您可以呼叫 `AfxThrowFileException` 函式。

## <a name="see-also"></a>另請參閱

[CFile 類別](../mfc/reference/cfile-class.md)<br/>
[檔案檔案::開啟](../mfc/reference/cfile-class.md#open)<br/>
[檔案](../mfc/files-in-mfc.md)
