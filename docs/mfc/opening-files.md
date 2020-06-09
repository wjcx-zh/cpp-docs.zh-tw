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
ms.openlocfilehash: 73407eba802b7640e880b821144954fa6442f177
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622156"
---
# <a name="opening-files"></a>開啟檔案

在 MFC 中，最常見的開啟檔案方式是一個兩階段的程序。

#### <a name="to-open-a-file"></a>開啟檔案

1. 建立檔案物件，而不指定路徑或使用權限旗標。

   您通常會藉由在堆疊框架上宣告[CFile](reference/cfile-class.md)變數來建立檔案物件。

1. 呼叫 file 物件的[Open](reference/cfile-class.md#open)成員函式，並提供路徑和許可權旗標。

   如果已成功開啟檔案，`Open` 會傳回非零值，如果無法開啟指定的檔案則會傳回 0。 `Open` 成員函式的原型如下：

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   開啟旗標指定您要為檔案指定的使用權限，例如唯讀。 可能的旗標值會在 `CFile` 類別中定義為列舉常數，使其符合 "`CFile::`" 的格式，如 `CFile::modeRead`。 如果您要建立檔案，請使用 `CFile::modeCreate` 旗標。

下列範例顯示如何建立具有讀取/寫入權限的新檔案 (取代任何具有相同路徑的舊檔案)：

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> 這個範例會建立並開啟檔案。 如果發生問題，則 `Open` 可能會在它的最後一個參數中傳回 `CFileException` 物件，如下所示。 TRACE 宏會同時列印檔案名和指出失敗原因的程式碼。 如果需要更詳細的錯誤報告，您可以呼叫 `AfxThrowFileException` 函式。

## <a name="see-also"></a>另請參閱

[CFile 類別](reference/cfile-class.md)<br/>
[CFile：： Open](reference/cfile-class.md#open)<br/>
[檔案](files-in-mfc.md)
