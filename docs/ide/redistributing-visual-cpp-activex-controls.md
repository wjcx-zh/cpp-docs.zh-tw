---
title: 轉散發 Visual C++ ActiveX 控制項 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331015"
---
# <a name="redistributing-visual-c-activex-controls"></a>轉散發 Visual C++ ActiveX 控制項
Visual C++ 6.0 提供您可以在後來要轉散發的應用程式中使用的 ActiveX 控制項。 Visual C++ 已不再包含這些控制項。 根據 Visual C++ 6.0 的授權合約，您可以與使用 Visual C++ 開發的應用程式一起轉散發這些控制項。  
  
> [!NOTE]
>  Microsoft 已不再支援 Visual C++ 6.0。  
  
 如需可轉散發 Visual C++ 6.0 ActiveX 控制項的清單，請參閱 Visual c + + 6.0 產品 CD 光碟 1 上的 Common\Redist\Redist.txt。  
  
 散發應用程式時，您必須安裝並註冊 ActiveX 控制項的 .ocx (使用 Regsvr32.exe)。 此外，您應該確定目標電腦有下列系統檔案的目前版本 (星號表示檔案需要註冊)：  
  
-   Asycfilt.dll  
  
-   Comcat.dll *  
  
-   Oleaut32.dll *  
  
-   Olepro32.dll *  
  
-   Stdole2.tlb  
  
 無法在目標系統上使用這些 DLL 時，您需要使用更新對應作業系統指定的機制來更新它們。 您可以從 [http://windowsupdate.microsoft.com ](http://windowsupdate.microsoft.com) 下載 Windows 作業系統的最新 Service Pack。  
  
 如果您的應用程式使用其中一個會連接到資料庫的 ActiveX 控制項，您必須在目標系統上安裝 Microsoft Data Access Components (MDAC)。 如需詳細資訊，請參閱[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)。  
  
 使用會連接至資料庫的 ActiveX 控制項時，您也需要在目標電腦上複寫資料來源名稱。 您可以透過 `ConfigDSN`　等函式，利用程式設計方式來執行這項作業。  
  
 某些可轉散發 ActiveX 控制項有其他相依性。 針對 Visual C++ 6.0 產品 CD 上 Os\System 資料夾中的每個 .ocx 檔，另外還有一個 .dep 檔。 針對您想要轉散發的每個 .ocx 檔，在對應的 .dep 檔中尋找一或多個 USES 項目。 如果已列出檔案，您必須確定檔案是在目標電腦上。 直接支援 .ocx 檔的任何 DLL 都必須註冊。 (Regsvr32.exe 若要成功，目標電腦必須先包含控制項以靜態方式載入的所有 DLL。)此外，如果列為相依性的 DLL 在 Visual C++ 6.0 CD 上的 Os\System 資料夾中也有 .dep 檔，則您也必須為 USES 項目調查該 .dep 檔。  
  
## <a name="see-also"></a>請參閱  
 [轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)