---
title: 略過序列化機制
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
ms.openlocfilehash: f47cac34f6cdbdae01af98ec28be5af17edf0e25
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620969"
---
# <a name="bypassing-the-serialization-mechanism"></a>略過序列化機制

如您所見，架構提供了預設的方式從檔案讀取和寫入資料。 將封存物件序列化符合許許多多應用程式的需求。 這類應用程式會將檔案完全讀入記憶體，讓使用者更新檔案，然後再將更新的版本寫入磁碟。

不過，部分應用程式是以非常不同的方式處理資料，而對這些應用程式將封存序列化就不適當。 範例包含資料庫程式、僅編輯大型檔案的一部分的程式、僅寫入純文字檔的程式以及共用資料檔的程式。

在這些情況下，您可以用不同的方式覆寫[序列化](reference/cobject-class.md#serialize)函式，以透過[CFile](reference/cfile-class.md)物件（而不是[CArchive](reference/carchive-class.md)物件）來協調檔案動作。

您可以使用 `Open` 類別的、 `Read` 、 `Write` 、和成員函式 `Close` `Seek` `CFile` 來開啟檔案、將檔案指標（搜尋）移至檔案中的特定點、在該時間點讀取一筆記錄（指定的位元組數）、讓使用者更新記錄，然後再次搜尋到相同的時間點，並將記錄寫回檔案。 架構會為您開啟檔案，所以您可以使用類別 `GetFile` 的 `CArchive` 成員函式取得 `CFile` 物件的指標。 如需更複雜且更有彈性的用法，您可以覆寫類別的[OnOpenDocument](reference/cdocument-class.md#onopendocument)和[OnSaveDocument](reference/cdocument-class.md#onsavedocument)成員函式 `CWinApp` 。 如需詳細資訊，請參閱*MFC 參考*中的類別[CFile](reference/cfile-class.md) 。

在此案例中，您的 `Serialize` 覆寫不會執行任何動作，除非例如您在文件關閉時要其讀取和寫入檔案標頭以使其保持最新。

## <a name="see-also"></a>另請參閱

[使用文件](using-documents.md)
