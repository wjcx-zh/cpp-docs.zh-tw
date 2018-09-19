---
title: 建立提供者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3149e59a239401c7c847da9371619821824a5d37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032090"
---
# <a name="creating-the-provider"></a>建立提供者

#### <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>若要使用 ATL OLE DB 提供者精靈建立 OLE DB 提供者  
  
1. 以滑鼠右鍵按一下專案。  
  
1. 在捷徑功能表，按一下 **新增**，然後按一下**加入類別**。  
  
1. 在 **加入類別**對話方塊中，選取**ATL OLE DB 提供者**圖示，，然後按一下**開啟**。  
  
1. 在 ATL OLE DB 提供者精靈，輸入您的提供者中的簡短名稱**簡短名稱** 方塊中。 下列主題會使用的簡稱 「 MyProvider"，但您可以使用另一個名稱。 其他名稱方塊中填入根據您所輸入的名稱。  
  
1. 如有需要請編輯其他名稱方塊。 除了物件和檔案名稱，您可以編輯下列項目：  
  
    -   **Coclass**: COM 用來建立提供者的名稱。  
  
    -   **ProgID**： 是可用來代替 GUID 的文字字串的程式設計識別項。  
  
    -   **版本**： 使用 ProgID 和 coclass 用以產生 版本相依程式設計識別碼。  
  
1. 按一下 [ **完成**]。  
  
## <a name="see-also"></a>另請參閱  

[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)