---
title: 提供者建立專案 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 86f85b95b4b45624a778bc183cabadda886d002d
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990079"
---
# <a name="creating-a-project-for-the-provider"></a>為提供者建立專案

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>若要建立的 OLE DB 提供者所在的專案  
  
1. 從 [檔案] 功能表中，依序按一下 [新增] 和 [專案]。  
  
     [ **新增專案** ] 對話方塊隨即出現。  
  
1. 在 **專案類型**窗格中，按一下**已安裝** > **Visual c + +** > **MFC/ATL**資料夾。 在 **範本**窗格中，按一下**ATL 專案**。  

    > [!NOTE]
    > 在舊版的 Visual Studio 中，尋找 專案類型之下**已安裝** > **範本** > **Visual c + +**  > **ATL**。
  
1. 在 **名稱**方塊中，輸入專案的名稱，然後按一下**確定**。  
  
     **ATL 專案精靈**隨即出現。  
  
1. 在  **ATL 專案精靈**，選擇**動態連結程式庫 (DLL)** for**應用程式類型**。  
  
1. 按一下 [ **完成**]。  
  
## <a name="see-also"></a>另請參閱  

[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)