---
title: ODBC 管理員
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
ms.openlocfilehash: ac893981ff8c697dc090f1e6ad5ac61886a69f99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395842"
---
# <a name="odbc-administrator"></a>ODBC 管理員

ODBC 管理員登錄和設定[zdroje dat](../../data/odbc/data-source-odbc.md)可供您在本機或網路上。 精靈會使用 ODBC 管理員所提供的資訊來建立您的使用者連接到資料來源的應用程式中的程式碼。

若要設定 ODBC 資料來源用於 MFC ODBC 類別或 MFC 資料存取物件 (DAO) 類別，您必須先註冊，並設定資料來源。 您可以使用 ODBC 管理員來新增和移除資料來源。 根據 ODBC 驅動程式，您也可以建立新的資料來源。

ODBC 管理員會在安裝期間安裝。 如果您選擇**自訂**安裝，且未選取任何的 ODBC 驅動程式，在**資料庫選項** 對話方塊中，您需要重新執行安裝程式安裝必要的檔案。

在安裝期間，您可以選取您想要安裝的 ODBC 驅動程式。 您稍後可以安裝其他驅動程式隨附的視覺化C++使用視覺效果C++安裝程式。

如果您想要安裝 ODBC 驅動程式不要使用尚未發行的視覺效果C++，您必須執行安裝程式隨附的驅動程式。

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>若要安裝 ODBC 驅動程式隨附具有視覺效果C++

1. 執行安裝程式，從您的視覺效果C++發佈 CD。

   開啟安裝程式中的對話方塊會隨即出現。

1. 按一下 [**下一步**在每個對話方塊中，直到您到達**安裝選項**] 對話方塊。 選取 [**自訂**，然後按一下**下一步]**。

1. 清除所有核取方塊後**Microsoft VisualC++安裝程式**對話方塊中，除了**資料庫選項**核取方塊，然後按一下**詳細資料**顯示**資料庫選項** 對話方塊。

1. 清除**Microsoft Data Access Objects**核取方塊，選取**Microsoft ODBC 驅動程式**核取方塊，然後按一下**詳細資料**。

   **Microsoft ODBC Drivers**  對話方塊隨即出現。

1. 選取您想要安裝，然後按一下 驅動的程式**確定**兩次。

1. 按一下 [**下一步]** 上其餘的對話方塊，開始安裝。 安裝完成時，安裝程式會通知您。

安裝驅動程式之後，您可以設定資料來源使用 ODBC 管理員。 在控制台中，您會發現 [ODBC] 圖示。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)