---
title: "建立提供者 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5521215560c84c19f7b661f0c9662752374b68e4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="creating-the-provider"></a>建立提供者
#### <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>若要使用 ATL OLE DB 提供者精靈建立 OLE DB 提供者  
  
1.  以滑鼠右鍵按一下專案。  
  
2.  在捷徑功能表，按一下 **新增**，然後按一下 **加入類別**。  
  
3.  在**加入類別**對話方塊中，選取**ATL OLE DB 提供者**圖示，然後再按一下**開啟**。  
  
4.  在 ATL OLE DB 提供者精靈中，輸入您的提供者中的簡短名稱**簡短名稱**方塊。 下列主題會使用簡短名稱"MyProvider"，但您可以使用另一個名稱。 其他名稱方塊中填入根據您輸入的名稱。  
  
5.  視需要編輯其他名稱方塊。 除了物件和檔案名稱，您可以編輯下列各項：  
  
    -   **Coclass**: COM 用來建立提供者的名稱。  
  
    -   **ProgID**： 是可用來代替 GUID 的文字字串的程式設計識別項。  
  
    -   **版本**: coclass ProgID 與用來產生版本相依程式設計識別碼。  
  
6.  按一下 [ **完成**]。  
  
## <a name="see-also"></a>請參閱  
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)