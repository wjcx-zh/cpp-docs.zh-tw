---
title: 建置系統變更 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.msbuild.changes
dev_langs:
- C++
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59d30e2afd07c21cb42dbc2b9109d7547d6c5b9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="build-system-changes"></a>建置系統變更
MSBuild 系統用於建置 Visual C++ 專案。 不過，在 Visual Studio 2008 和較早版本使用 VCBuild 系統。 某些檔案類型和依賴 VCBuild 的概念已不存在，或是目前系統的表示方式。 本文件討論了目前建置系統中的差異。  
  
## <a name="vcproj-is-now-vcxproj"></a>.vcproj 現在是.vcxproj  
 專案檔無法再使用.vcproj 檔案的副檔名。 Visual Studio 會自動將所建立的是舊版 Visual c + + 格式，以供目前系統的專案檔。 如需如何手動升級專案的詳細資訊，請參閱[/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe)。  
  
 在目前版本中，專案檔的副檔名為.vcxproj。  
  
## <a name="vsprops-is-now-props"></a>.vsprops 現在是.props  
 在舊版中，*專案屬性工作表*是以 XML 為基礎的檔案具有.vsprops 檔案的副檔名。 專案屬性工作表，可讓您指定的建置工具，例如編譯器或連結器參數，以及建立使用者定義巨集。  
  
 目前版本中，在專案屬性工作表的副檔名會是.props。  
  
## <a name="custom-build-rules-and-rules-files"></a>自訂建置規則和.rules 檔案  
 在舊版中，*規則檔*是以 XML 為基礎的檔案具有.rules 檔案的副檔名。 規則檔案可讓您定義自訂建置規則，並將其合併至 Visual c + + 專案的建置程序。 自訂建置規則，它可以是與一個或多個檔案名稱的副檔名相關聯，可讓您將輸入的檔傳遞至一種工具，會建立一個或多個輸出檔案。  
  
 在此版本中，自訂建置規則會以三種檔案類型、.xml、.props 和.targets，而不是.rules 檔案。 當您使用舊版 Visual c + + 所建立的.rules 檔案移轉至目前版本相等的.xml、.props 和.targets 檔案建立和儲存在您的專案，以及原始.rules 檔案中。  
  
> [!IMPORTANT]
>  在目前版本中，[!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)] 不支援建立新規則。 因此，若要使用以舊版 Visual C++ 所建立之專案的規則檔，最簡單的方式就是將專案移轉為目前版本。  
  
## <a name="inheritance-macros"></a>繼承巨集  
 在舊版中， **$ （inherit)**巨集由專案建置系統命令列上指定繼承的屬性出現的順序。 **$ （noinherit)**巨集 $ （inherit） 来忽略的任何項目會導致並造成繼承，不會繼承任何屬性。 例如，根據預設 $ （inherit） 巨集會利用指定的檔案[（其他 Include 目錄） /I](../build/reference/i-additional-include-directories.md)来附加至命令列編譯器選項。  
  
 在目前版本中，藉由指定屬性的值串連的一個或多個常值和屬性的巨集以支援繼承。 **$ （inherit)**和**$ （noinherit)**巨集不支援。  
  
 在下列範例中，以分號分隔的清單被指派給屬性頁上的屬性。 清單所組成的串連*\<值 >*常值和值`MyProperty`屬性，會使用巨集標記法來存取， **$(** *MyProperty***)**。  
  
```  
Property=<value>;$(MyProperty)  
```  
  
## <a name="vcxprojuser-files"></a>。.vcxproj.user 檔案  
 使用者檔案 (。.vcxproj.user) 會儲存使用者特定的屬性，例如偵錯和部署設定。 .Vcxproj.user 檔案適用於所有專案特定的使用者。  
  
## <a name="vcxprojfilters-file"></a>。 vcxproj.filters 檔案  
 當**方案總管 中**用來將檔案加入專案時，篩選檔 (。 vcxproj.filters) 定義中的 where**方案總管 中**樹狀的檢視新增檔案時，根據檔案的副檔名。  
  
## <a name="vc-directories-settings"></a>VC + + 目錄設定  
 Visual c + + 目錄設定中指定[VC + + 目錄屬性頁](../ide/vcpp-directories-property-page.md)。 在舊版的 Visual Studio 中，目錄設定適用於每個使用者，並已排除的目錄清單指定 sysincl.dat 檔案中。  
  
 您無法變更的 VC + + 目錄設定，如果您執行[devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe)在命令列。 您也無法變更設定如果您開啟**工具**功能表上，按一下 **匯入和匯出設定**，然後選取**重設所有設定**選項。  
  
 移轉 VC + + 目錄設定從舊版 Visual c + + 所建立的.vssettings 檔。 開啟**工具**功能表上，按一下 **匯入和匯出設定**，選取**匯入選取的環境設定**，然後依照精靈的指示進行。 當您啟動 Visual Studio，在第一次上或**選擇預設環境設定**對話方塊中，選取**從舊版移轉我符合資格的設定，並將其套用的預設值下面選取**。  
  
## <a name="see-also"></a>請參閱  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)