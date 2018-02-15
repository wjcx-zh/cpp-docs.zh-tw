---
title: -SUBSYSTEM | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /subsystem
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 945e0d6da5ff1c5f24f8c0e10693f06334e0a25c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="subsystem"></a>/SUBSYSTEM
指定可執行映像所需的執行環境。  
  
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|  
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]  
```  
  
## <a name="remarks"></a>備註  
 這個選項可編輯影像，指出作業系統必須叫用哪個子系統以執行。  
  
 您可以指定下列任何子系統：  
  
 BOOT_APPLICATION  
 在 Windows 開機環境中執行的應用程式。 如需開機應用程式的詳細資訊，請參閱[關於 BCD WMI 提供者](http://msdn.microsoft.com/library/aa362639.aspx)。  
  
 主控台  
 Windows 字元模式應用程式。 作業系統會提供主控台的主控台應用程式。  
  
 可延伸韌體介面 (EFI) 影像  
 EFI 子系統選項說明可延伸韌體介面環境中執行的可執行檔影像。 這種環境通常提供硬體，並在載入作業系統之前執行。 EFI 影像類型之間的主要差異是載入影像的記憶體位置，和呼叫影像時傳回時所採取的動作。 控制權傳回時會卸載 EFI_APPLICATION 影像。 只有當控制項傳回錯誤碼時，EFI_BOOT_SERVICE_DRIVER 或 EFI_RUNTIME_DRIVER 才會卸載。 從 ROM 執行 EFI_ROM 影像。 如需詳細資訊，請參閱規格上[Unified EFI 論壇](http://www.uefi.org/)網站。  
  
 原生  
 在沒有子系統環境中執行的程式碼 — 例如，核心模式裝置驅動程式和原生系統處理序。 這個選項通常保留給 Windows 系統功能。  
  
 POSIX  
 在 Windows 中 POSIX 子系統中執行的應用程式。  
  
 WINDOWS  
 在 Windows 圖形化環境中執行的應用程式。 這包括桌面應用程式和通用 Windows 平台 (UWP) 應用程式。  
  
 WINDOWSCE  
 WINDOWSCE 子系統指出應用程式應在有 Windows CE 核心版本的裝置上執行。 核心版本包含 PocketPC、Windows Mobile、Windows Phone 7、Windows CE V1.0-6.0R3 和 Windows Embedded Compact 7。  
  
 選擇性 `major` 和 `minor` 值指定了指定子系統的最小必要版本：  
  
-   版本號碼的整數部分 (小數點左邊的部分) 由 `major` 表示。  
  
-   版本號碼的小數部分 (小數點右邊的部分) 由 `minor` 表示。  
  
-   值 `major` 和 `minor` 必須是從 0 到 65535。  
  
 子系統的選擇會影響程式的預設開始位址。 如需詳細資訊，請參閱[/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)，連結器 /ENTRY:*函式*選項。  
  
 如需詳細資訊，包括每個子系統的主要和次要版本號碼的最小值和預設值，請參閱[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)連結器選項。  
  
## <a name="see-also"></a>請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)