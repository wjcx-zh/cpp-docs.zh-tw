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
ms.openlocfilehash: 9e88492919eac80a4f3db2f94202d49011aa69de
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213154"
---
# <a name="odbc-administrator"></a>ODBC 管理員

ODBC 系統管理員會在本機或網路上註冊並設定可供您使用的[資料來源](../../data/odbc/data-source-odbc.md)。 這些嚮導會使用 ODBC 管理員所提供的資訊，在您的應用程式中建立可將使用者連接至資料來源的程式碼。

若要設定 ODBC 資料來源以與 MFC ODBC 類別或 MFC 資料存取物件（DAO）類別搭配使用，您必須先註冊並設定資料來源。 使用 ODBC 管理員來新增和移除資料來源。 視 ODBC 驅動程式而定，您也可以建立新的資料來源。

在安裝期間會安裝 ODBC 系統管理員。 如果您選擇 [**自訂**安裝]，但未選取 [**資料庫選項**] 對話方塊中的任何 ODBC 驅動程式，您必須再次執行安裝程式以安裝必要的檔案。

在安裝期間，您會選取想要安裝的 ODBC 驅動程式。 您稍後可以使用視覺效果C++ C++安裝程式，安裝 visual 隨附的其他驅動程式。

如果您想要安裝未隨附于 Visual C++的 ODBC 驅動程式，您必須執行驅動程式隨附的安裝程式。

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>安裝隨附于 Visual 的 ODBC 驅動程式C++

1. 從您的視覺效果C++散發光碟執行安裝程式。

   安裝程式中的 [開啟] 對話方塊隨即出現。

1. 在每個對話方塊上按 **[下一步**]，直到您到達 [**安裝選項**] 對話方塊。 選取 [**自訂**]，然後按 **[下一步]** 。

1. 清除 [ **Microsoft C++視覺效果安裝程式**] 對話方塊中 [**資料庫選項**] 核取方塊以外的所有核取方塊，然後按一下 [**詳細資料**] 以顯示 [**資料庫選項**] 對話方塊。

1. 清除 [ **Microsoft 資料存取物件**] 核取方塊，選取 [ **Microsoft ODBC 驅動程式**] 核取方塊，然後按一下 [**詳細資料**]。

   [ **MICROSOFT ODBC 驅動程式**] 對話方塊隨即出現。

1. 選取您要安裝的驅動程式，然後按兩次 **[確定]** 。

1. 在其餘的對話方塊上按 **[下一步**] 開始安裝。 安裝完成時，安裝程式會通知您。

安裝驅動程式時，您可以使用 ODBC 管理員來設定資料來源。 您會在 [控制台] 中找到 [ODBC] 圖示。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)
