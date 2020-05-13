---
title: ODBC 類別和執行緒
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: aaf54a3a1d616cde5742dad45955bd415f612d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368693"
---
# <a name="odbc-classes-and-threads"></a>ODBC 類別和執行緒

從 MFC 4.2 開始,MFC ODBC 類具有多線程支援。 但是請注意,MFC 不為 DAO 類提供多線程支援。

ODBC 類的多線程支援有一些限制。 由於這些類包裝了ODBC API,因此它們僅限於構建它們的元件的多線程支援。 例如,許多 ODBC 驅動程式不是線程安全的;因此,許多 ODBC 驅動程式並不安全。因此,如果將 MFC ODBC 類與其中一個驅動程式一起使用,則它們不是線程安全的。 您應該驗證您的特定驅動程式是否為線程安全。

創建多線程應用程式時,在使用多個線程操作同一物件時應非常小心。 例如,在兩個線程`CRecordset`中使用同一物件可能會導致檢索數據時出現問題;因此,在兩個線程中使用相同的物件可能會導致問題。一個線程中的提取操作可能會覆蓋另一個線程中獲取的數據。 在單獨的線程中,MFC ODBC 類更常見的用途是跨線`CDatabase`程共用 打開的物件,以使用相同的 ODBC 連接`CRecordset`,每個線程中 都有單獨的物件。 請注意,不應將未打開`CDatabase`的物件傳遞給另一`CRecordset`個 線程中的物件。

> [!NOTE]
> 如果必須有多個線程操作同一物件,則應實現相應的同步機制,如關鍵部分。 請注意,某些操作(如`Open`)不受保護。 應確保這些操作不會同時從單獨的線程調用。

有關建立多線程式的詳細資訊,請參閱[多線程式主題](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[開放資料庫連線 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[資料存取程式設計(MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
