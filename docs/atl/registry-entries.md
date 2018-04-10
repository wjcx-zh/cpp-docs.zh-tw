---
title: 登錄項目 (ATL) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: faef0ca0c1c9c4c2986a039b8b1a26517641acd0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="registry-entries"></a>登錄項目
DCOM 導入的應用程式識別碼 (Appid)，群組的一或多個 DCOM 物件在登錄中的集中式位置的組態選項的概念。 您可以在名為物件的 CLSID 下值的 AppID 中其值，指出指定 AppID。  
  
 根據預設，ATL 產生的服務會使用 CLSID 為它的 AppID 的 guid。 在下`HKEY_CLASSES_ROOT\AppID`，您可以指定特定的 DCOM 項目。 一開始，有兩個項目：  
  
-   `LocalService`與服務的名稱相同的值。 如果此值存在，它會使用而不是`LocalServer32`CLSID 下索引鍵。  
  
-   `ServiceParameters`其值等於與`-Service`。 這個值會指定在啟動時傳遞至服務的參數。 請注意，這些參數會傳遞至服務的`ServiceMain`函式，未`WinMain`。  
  
 任何 DCOM 服務也需要建立另一個索引鍵下的`HKEY_CLASSES_ROOT\AppID`。 這個索引鍵是等於的可執行檔的名稱，做為交互參照，因為它包含 AppID 值，指出 AppID 項目。  
  
## <a name="see-also"></a>請參閱  
 [服務](../atl/atl-services.md)

