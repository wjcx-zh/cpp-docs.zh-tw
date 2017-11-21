---
title: "ODBC 管理員 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 834825b38eb8d5c81752dfed85f44202fbce3299
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="odbc-administrator"></a>ODBC 管理員
ODBC 管理員註冊及設定[資料來源](../../data/odbc/data-source-odbc.md)可供您在本機或網路上。 精靈會在您的使用者連接到資料來源的應用程式中建立的程式碼使用 ODBC 管理員所提供的資訊。  
  
 若要設定為使用 MFC ODBC 類別或 MFC 資料存取物件 (DAO) 類別的 ODBC 資料來源，您必須先註冊及設定資料來源。 使用 ODBC 管理員加入和移除資料來源。 根據 ODBC 驅動程式，您也可以建立新的資料來源。  
  
 ODBC 管理員會在安裝期間安裝。 如果您選擇**自訂**安裝，且未選取任何 ODBC 驅動程式**資料庫選項**對話方塊，您需要執行安裝程式以安裝必要的檔案。  
  
 在安裝期間，您可以選取您想要安裝的 ODBC 驅動程式。 您稍後可以安裝其他驅動程式隨附於 Visual c + + 使用 Visual c + + 安裝程式。  
  
 如果您想要使用 Visual c + + 安裝不要的 ODBC 驅動程式，您必須執行安裝程式隨附的驅動程式。  
  
#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>若要安裝 Visual c + + 隨附的 ODBC 驅動程式  
  
1.  從您的 Visual c + + 發佈光碟片執行安裝程式。  
  
     開啟安裝程式 對話方塊會隨即出現。  
  
2.  按一下**下一步**在每個對話方塊中，直到您到達**安裝選項** 對話方塊。 選取**自訂**，然後按一下  `Next`。  
  
3.  清除所有核取方塊**Microsoft Visual c + + 安裝程式**對話方塊中，除了**資料庫選項**核取方塊，然後**詳細資料**顯示**資料庫選項** 對話方塊。  
  
4.  清除**Microsoft 資料存取物件**核取方塊，選取**Microsoft ODBC 驅動程式**核取方塊，然後**詳細資料**。  
  
     **Microsoft ODBC 驅動程式** 對話方塊隨即出現。  
  
5.  選取您想要安裝，然後按一下 驅動的程式**確定**兩次。  
  
6.  按一下**下一步**上開始安裝其餘的對話方塊。 安裝完成時，安裝程式會通知您。  
  
 安裝驅動程式之後，您可以設定資料來源使用 ODBC 管理員。 在控制台中，您會發現 [ODBC] 圖示。  
  
## <a name="see-also"></a>另請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)