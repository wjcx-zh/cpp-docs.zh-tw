---
title: DCOMCNFG
ms.date: 11/04/2016
f1_keywords:
- DCOMCNFG
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
ms.openlocfilehash: 8bf85c32093051b124d007a04eed2bbf10a56039
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552642"
---
# <a name="dcomcnfg"></a>DCOMCNFG

DCOMCNFG 是 Windows NT 4.0 公用程式，可讓您在登錄中設定各種 DCOM 特有的設定。 [DCOMCNFG] 視窗有三個頁面： 預設的安全性、 預設的內容和應用程式。 在 Windows 2000 第四個頁面上，預設的通訊協定，會出現。

## <a name="default-security-page"></a>預設 [安全性] 頁面

您可以使用 [預設的安全性] 頁面來指定物件的預設權限的系統上。 預設安全性 頁面有三個區段： 存取、 啟動和組態。 若要變更區段的預設值，請按一下 [對應**編輯預設**] 按鈕。 這些預設安全性設定會儲存在登錄中`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`。

## <a name="default-protocols-page"></a>預設通訊協定 頁面

此頁面會列出可由 DCOM 使用這部電腦上的網路通訊協定的集合。 順序會反映在其中，將會使用; 的優先順序在清單中的第一個具有最高優先權。 通訊協定可以加入或刪除從這個頁面。

## <a name="default-properties-page"></a>預設屬性頁面

在預設內容 頁面上，您必須選取**這部電腦上啟用分散式 COM**核取方塊，如果您想在這部電腦上執行的存取 COM 物件的其他電腦上的用戶端。 選取這個選項會設定`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM`值`Y`。

## <a name="applications-page"></a>應用程式 頁面

您變更應用程式 頁面的特定物件的設定。 只要從清單中選取 [應用程式，並按一下**屬性**] 按鈕。 [屬性] 視窗有五個的頁面：

- [一般] 頁面會確認您正在使用的應用程式。

- [位置] 頁面可讓您指定應在何處應用程式執行時用戶端呼叫`CoCreateInstance`上相關的 CLSID。 如果您選取**下列電腦上執行的應用程式**核取方塊，然後輸入電腦名稱，則會顯示`RemoteServerName`值會新增至該應用程式的 AppID。 清除**這部電腦上執行應用程式** 核取方塊重新命名`LocalService`值`_LocalService`，藉此，則會停用。

- 安全性 頁面是預設安全性 頁面中 DCOMCNFG 視窗中，找到類似，不同之處在於這些設定僅適用於目前的應用程式。 同樣地，設定會儲存在該物件的 AppID。

- 身分識別 頁面會識別哪些使用者用來執行應用程式。

- [端點] 頁面會列出一組通訊協定和適用於所選的 DCOM 伺服器的用戶端的端點。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)

