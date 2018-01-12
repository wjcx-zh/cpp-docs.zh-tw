---
title: "編譯器和連結器選項 (C + + /CX) |Microsoft 文件"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0dc7610b56d55fc5d42a0c4b73a5405be3d4dda9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-and-linker-options-ccx"></a>編譯器和連結器選項 (C++/CX)
環境變數，C + + /CX 編譯器選項和連結器選項均支援的應用程式建置為 Windows 執行階段。  
  
## <a name="library-path"></a>程式庫路徑  
 %LIBPATH% 環境變數指定 .winmd 檔案的預設搜尋路徑。  
  
## <a name="compiler-options"></a>編譯器選項  
  
|選項|描述|  
|------------|-----------------|  
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /ZW:nostdlib|啟用 Windows 執行階段語言擴充功能。<br /><br /> `nostdlib` 參數可防止編譯器使用標準、預先定義的搜尋路徑來尋找組件和 .winmd 檔案。<br /><br /> **/ZW** 編譯器選項會隱含指定下列編譯器選項：<br /><br /> -   **/FI** vccorlib.h，強制包含 vccorlib.h 標頭檔會定義由編譯器所需的許多類型。<br />-   [/FU](../build/reference/fu-name-forced-hash-using-file.md) Windows.winmd，強制包含 Windows.winmd 中繼資料檔案由作業系統提供，並定義 Windows 執行階段中的許多類型。<br />-   **/FU** Platform.winmd，強制包含 Platform.winmd 中繼資料檔，此檔案由編譯器提供，且定義 Platform 命名空間系列中的大部分類型。|  
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|將以 *dir* 參數指定的目錄加入搜尋路徑中，供編譯器用來尋找組件和 .winmd 檔案。|  
|**/FU**  *檔案*|強制包含指定的模組或 .winmd 檔案。 也就是說，您不需要在原始程式碼中指定 `#using`*檔案* 。 編譯器會自動強制包含其本身的 Windows 中繼資料檔 Platform.winmd。|  
|/D "WINAPI_FAMILY=2"|建立可讓您使用與 Windows 執行階段相容的 Win32 sdk 子集的定義。|  
  
## <a name="linker-options"></a>連結器選項  
  
|選項|描述|  
|------------|-----------------|  
|/APPCONTAINER[:NO]|將可執行檔標記為可在 appcontainer 中執行 (僅限)。|  
|/ WINMD [: {否 &#124; 僅}]|發出 .winmd 檔案和相關聯的二進位檔。 這個選項必須傳遞至連結器，才能發出 .winmd。<br /><br /> **NO**- 不發出 .winmd 檔案，但發出二進位檔案。<br /><br /> **ONLY**- 發出 .winmd 檔案，但不發出二進位檔案。|  
|/WINMDFILE:*檔案名稱*|要發出的 .winmd 檔案名稱，而不是預設 .winmd 檔案名稱。 如果命令列上指定多個檔案名稱，則會使用最後一個名稱。|  
|/WINMDDELAYSIGN[:NO]|部分簽署 .winmd 檔案，並將公開金鑰放在二進位檔中。<br /><br /> **NO**- (預設值) 不簽署 .winmd 檔案。<br /><br /> 除非同時指定 /WINMDKEYFILE 或 /WINMDKEYCONTAINER，否則 /WINMDDELAYSIGN 沒有作用。|  
|/WINMDKEYCONTAINER:*name*|指定用於簽署組件的金鑰容器。 *name* 參數對應至用於簽署中繼資料檔的金鑰容器。|  
|/WINMDKEYFILE:*filename*|指定用於簽署組件的金鑰或金鑰組。 *檔案名稱* 參數對應至用於簽署中繼資料檔的金鑰。|  
  
### <a name="remarks"></a>備註  
 當您使用 **/ZW**時，編譯器會自動連結至 C 執行階段 (CRT) 的 DLL 版本。 不允許連結至靜態程式庫版本，並使用通用 Windows 平台應用程式中不允許的 CRT 函任何的式會造成編譯時期錯誤。  
  
## <a name="see-also"></a>請參閱  
 [建置應用程式和程式庫](../cppcx/building-apps-and-libraries-c-cx.md)