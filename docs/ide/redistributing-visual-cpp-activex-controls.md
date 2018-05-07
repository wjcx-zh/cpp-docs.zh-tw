---
title: 轉散發 Visual c + + ActiveX 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b770bbacca06c6edfb3b9b4eda53fc7be8a7ae0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="redistributing-visual-c-activex-controls"></a>轉散發 Visual C++ ActiveX 控制項
Visual c + + 6.0 提供 ActiveX 控制項，然後重新發佈的應用程式中，您可以使用。 Visual c + + 已不再包含這些控制項。 每個 Visual c + + 6.0 授權合約，您可以與 Visual c + + 開發的應用程式轉散發這些控制項。  
  
> [!NOTE]
>  Microsoft 不再支援 visual c + + 6.0。  
  
 如需可轉散發 Visual c + + 6.0 ActiveX 控制項的清單，請參閱 Common\Redist\Redist.txt 光碟 1 的 Visual c + + 6.0 產品 CD 上。  
  
 當散發應用程式，您必須安裝並註冊 ActiveX 控制項 （使用 Regsvr32.exe）.ocx 一起提供。 此外，您應該確定目標電腦有下列的系統檔案 （以星號表示檔案需要註冊） 的目前版本：  
  
-   asycfilt.dll  
  
-   Comcat.dll *  
  
-   Oleaut32.dll *  
  
-   Olepro32.dll *  
  
-   stdole2.tlb  
  
 無法在目標系統上使用這些 Dll 時，您需要取得這些使用規定的機制來更新對應的作業系統更新。 您可以下載最新 service pack 的 Windows 作業系統從[ http://windowsupdate.microsoft.com ](http://windowsupdate.microsoft.com)。  
  
 如果您的應用程式使用其中一個會連接到資料庫的 ActiveX 控制項，您必須具有 Microsoft Data Access Components (MDAC) 目標系統上安裝。 如需詳細資訊，請參閱[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)。  
  
 當使用 ActiveX 控制項連接至資料庫時，您也需要複寫目標電腦上的資料來源名稱。 您可以透過程式設計方式與函式例如`ConfigDSN`。  
  
 某些可轉散發 ActiveX 控制項有其他相依性。 每個.ocx 檔案 Os\System 資料夾中 Visual c + + 6.0 產品 CD 上，另外還有.dep 檔案。 針對每個您想要重新發佈的.ocx 檔案，尋找對應的.dep 檔案中的一個或多個使用項目。 如果列出的檔案，您必須確定檔案是在目標電腦上。 直接支援.ocx 檔案必須已註冊的任何 Dll。 （成功 Regsvr32.exe，目標電腦必須先包含所有控制項以靜態方式載入的 Dll。）此外，如果列為相依的 DLL 也有.dep 檔案，在 Visual c + + 6.0 CD Os\System 資料夾中，您也必須調查.dep 檔案使用的項目。  
  
## <a name="see-also"></a>另請參閱  
 [轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)