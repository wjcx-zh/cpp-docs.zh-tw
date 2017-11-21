---
title: "WSADATA 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WSADATA
dev_langs: C++
helpviewer_keywords: WSADATA structure [MFC]
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f74980fdecc1a3ed0045aad969bb7c015f64d80d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="wsadata-structure"></a>WSADATA 結構
`WSADATA` 結構用於儲存由呼叫傳回至 `AfxSocketInit` 全域函式的 Windows 通訊端初始化資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct WSAData {  
    WORD wVersion;  
    WORD wHighVersion;  
    char szDescription[WSADESCRIPTION_LEN+1];  
    char szSystemStatus[WSASYSSTATUS_LEN+1];  
    unsigned short iMaxSockets;  
    unsigned short iMaxUdpDg;  
    char FAR* lpVendorInfo;  
};  
```  
  
#### <a name="parameters"></a>參數  
 *wVersion*  
 Windows 通訊端 DLL 要求呼叫端使用的 Windows 通訊端規格版本。  
  
 *wHighVersion*  
 這個 DLL 可支援的最高 Windows 通訊端規格版本 (編碼如上所示)。 一般來說，這是與相同**wVersion**。  
  
 *szDescription*  
 Windows 通訊端 DLL 在以 null 終止之 ASCII 字串複製 Windows Sockets 實作的描述，包括廠商身分識別。 文字 (長度最多 256 個字元) 可以包含任何字元，不過，廠商會被告誡包含控制項和格式化字元：應用程式最可能將此值顯示 (可能以截斷方式) 在狀態訊。  
  
 *szSystemStatus*  
 Windows 通訊端 DLL 在以 null 終止之 ASCII 字串複製相關狀態或組態資訊。 Windows Sockets DLL 的資訊可能會有所幫助使用者或支援人員; 時，才使用這個欄位不應視為，來擴充**szDescription**欄位。  
  
 *iMaxSockets*  
 單一處理序可能會開啟的最大通訊端數目。 Windows 通訊端實作可提供通訊端全域集區以配置到任何處理序，或者也依照通訊端的每個處理序資源進行配置。 數字完全反映 Windows 通訊端 DLL 或網路軟體組態的設定方式。 應用程式撰寫者可以使用這個數字當成 Windows Sockets 實作是否可由應用程式使用的指示。 例如，X Windows 伺服器可能會檢查**iMaxSockets**初次啟動時： 如果少於 8，應用程式會顯示錯誤訊息指示使用者重新設定網路軟體。 (這是在其中的狀況**szSystemStatus**文字可能會使用。)顯然並不保證特定應用程式可以實際配置**iMaxSockets**通訊端，因為可能有使用中的其他 Windows 通訊端應用程式。  
  
 *iMaxUdpDg*  
 可由 Windows 通訊端應用程式傳送或接收的最大使用者資料包通訊協定 (UDP) 資料包的位元組大小。 如果實作沒有施加限制， **iMaxUdpDg**為零。 在 Berkeley 通訊端的許多實作中，UDP 資料包上有 8192 位元組的隱含限制 (必要時會分散)。 Windows 通訊端實作可以根據片段重組緩衝區的配置施加限制。 最小值**iMaxUdpDg**相容的 Windows Sockets 實作是 512。 請注意，不論值**iMaxUdpDg**，不得嘗試傳送大於比最大傳輸單位 (MTU) 網路的廣播的資料包。 (Windows 通訊端 API 不提供機制來尋找 MTU，不過不得少於 512 位元組)。  
  
 *lpVendorInfo*  
 廠商特定資料結構的遠端指標。 這個結構的定義 (如果有提供) 超出 Windows 通訊端規格的範圍。  
  
> [!NOTE]
>  在 MFC 中，`WSADATA` 結構由以您的 `AfxSocketInit` 函式呼叫之 `InitInstance` 函式傳回。 如果您需要稍後使用資訊，您可以擷取結構並儲存在程式中。  
  
## <a name="requirements"></a>需求  
 **標頭：** winsock2.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)

