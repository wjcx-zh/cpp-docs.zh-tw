---
title: 轉散發 Visual C++ ActiveX 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: 4c7806502024789ed41f3043d7db6c87c7c71ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359872"
---
# <a name="redistributing-visual-c-activex-controls"></a>轉散發 Visual C++ ActiveX 控制項

Visual C++ 6.0 提供您可以在後來要轉散發的應用程式中使用的 ActiveX 控制項。 Visual C++ 已不再包含這些控制項。 根據 Visual C++ 6.0 的授權合約，您可以與使用 Visual C++ 開發的應用程式一起轉散發這些控制項。

> [!NOTE]
> Microsoft 已不再支援 Visual C++ 6.0。

如需可轉散發 Visual C++ 6.0 ActiveX 控制項的清單，請參閱 Visual c + + 6.0 產品 CD 光碟 1 上的 Common\Redist\Redist.txt。

散發應用程式時，您必須安裝並註冊 ActiveX 控制項的 .ocx (使用 Regsvr32.exe)。 此外，您應該確定目標電腦有下列系統檔案的目前版本 (星號表示檔案需要註冊)：

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

無法在目標系統上使用這些 DLL 時，您需要使用更新對應作業系統指定的機制來更新它們。 可以從下載 Windows 作業系統的最新[http://windowsupdate.microsoft.com](https://windowsupdate.microsoft.com)服務套件 。

使用會連接至資料庫的 ActiveX 控制項時，您也需要在目標電腦上複寫資料來源名稱。 您可以透過 `ConfigDSN`　等函式，利用程式設計方式來執行這項作業。

某些可轉散發 ActiveX 控制項有其他相依性。 針對 Visual C++ 6.0 產品 CD 上 Os\System 資料夾中的每個 .ocx 檔，另外還有一個 .dep 檔。 針對您想要轉散發的每個 .ocx 檔，在對應的 .dep 檔中尋找一或多個 USES 項目。 如果已列出檔案，您必須確定檔案是在目標電腦上。 直接支援 .ocx 檔的任何 DLL 都必須註冊。 (要使 Regsvr32.exe 成功,目標計算機必須首先包含控制項靜態載入的所有 DLL。此外,如果列為依賴項的 DLL 在 Visual C++ 6.0 CD 上的 Os_System 資料夾中也有 .dep 檔,則還必須調查該 .dep 檔以用於 USES 條目。

## <a name="see-also"></a>另請參閱

[轉散發 Visual C++ 檔案](redistributing-visual-cpp-files.md)
