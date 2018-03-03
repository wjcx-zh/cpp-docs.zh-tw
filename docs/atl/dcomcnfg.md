---
title: "DCOMCNFG |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DCOMCNFG
dev_langs:
- C++
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f40b372666ba2b623450eb0e58a6c0ff372559ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dcomcnfg"></a>DCOMCNFG
**DCOMCNFG**是 Windows NT 4.0 公用程式，可讓您在登錄中設定特定的 DCOM 的各種設定。 **DCOMCNFG**視窗有三頁： 預設安全性、 預設的內容和應用程式。 在 Windows 2000 第四個頁面上，預設的通訊協定，會出現。  
  
## <a name="default-security-page"></a>預設安全性頁面  
 您可以使用預設安全性 頁面來指定系統上的預設物件的權限。 預設安全性頁面有三個區段： 存取、 啟動和組態。 若要變更區段的預設值，請按一下 [對應**編輯預設值**] 按鈕。 這些預設安全性設定會儲存在登錄中`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`。  
  
## <a name="default-protocols-page"></a>預設通訊協定 頁面  
 此頁面列出可由 DCOM 使用這部電腦上的網路通訊協定的集合。 順序會反映在他們將使用; 的優先順序在清單中的第一個具有最高優先權。 通訊協定可以加入或刪除從這個頁面。  
  
## <a name="default-properties-page"></a>預設屬性頁面  
 在預設內容 頁面上，您必須選取**這台電腦上啟用分散式 COM**核取方塊，如果您想在這部電腦上執行的存取 COM 物件的其他電腦上的用戶端。 選取這個選項會設定`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM`值設定為`Y`。  
  
## <a name="applications-page"></a>應用程式 頁面  
 您變更之特定物件的應用程式 頁面設定。 只要從清單中選取應用程式，並按一下**屬性** 按鈕。 [屬性] 視窗有五個頁面：  
  
-   [一般] 頁面會確認您正在使用的應用程式。  
  
-   [位置] 頁面可讓您指定應在何處應用程式執行時用戶端呼叫`CoCreateInstance`上相關的 CLSID。 如果您選取**下列電腦上執行應用程式**核取方塊並輸入電腦名稱，則`RemoteServerName`值隨即新增至該應用程式的 AppID。 清除**這台電腦上執行應用程式**核取方塊重新命名`LocalService`值設定為`_LocalService`，藉此停用。  
  
-   [安全性] 頁面是預設的安全性頁面中找到類似**DCOMCNFG**視窗中，不同之處在於這些設定僅適用於目前的應用程式。 同樣地，設定會儲存在該物件的 AppID。  
  
-   身分識別 頁面會識別哪些使用者用來執行應用程式。  
  
-   [端點] 頁面會列出通訊協定和適用於所選的 DCOM 伺服器的用戶端端點的集合。  
  
## <a name="see-also"></a>請參閱  
 [服務](../atl/atl-services.md)

