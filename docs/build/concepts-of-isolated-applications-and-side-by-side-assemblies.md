---
title: 隔離的應用程式和並排顯示組件的概念 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62420838cca0bcb2a922b01c6951749de7449e81
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222457"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>隔離應用程式和並存組件的概念
應用程式會被視為[隔離的應用程式](/windows/desktop/SbsCs/isolated-applications)的所有元件是否[並排顯示組件](/windows/desktop/SbsCs/about-side-by-side-assemblies-)。 並存組件是資源的集合，是一組共同部署的 DLL、Windows 類別、COM 伺服器、類型程式庫或介面，可供應用程式在執行階段使用。 一般而言，並存組件是一至數個 DLL，  
  
## <a name="shared-or-private"></a>共用或私用  
 並存組件可以是共用或私用組件。 [共用的並排顯示組件](https://msdn.microsoft.com/library/aa375996.aspx)可能由多個應用程式在其資訊清單中，指定組件之相依性。 而同時間執行的不同應用程式，則可以共用並存組件的多個版本。 A[私用組件](/windows/desktop/SbsCs/about-private-assemblies-)是專供該應用程式的應用程式一起部署的組件。 私用組件會安裝在含有應用程式可執行檔的資料夾中，或是安裝在它的其中一個子資料夾中。  
  
## <a name="manifests-and-search-order"></a>資訊清單和搜尋順序  
 會描述隔離的應用程式和並排顯示組件[資訊清單](https://msdn.microsoft.com/library/aa375365)。 資訊清單是 XML 文件，它可以是外部檔案，也可以內嵌於應用程式中或組件中以做為資源。 隔離之應用程式的資訊清單檔是用來管理共用之並存組件的名稱和版本 (應用程式在執行階段應該要繫結至這個組件)。 並存組件的資訊清單會指定並存組件的名稱、版本、資源和相依組件。 如果是共用並存組件，它的資訊清單會安裝在 %WINDIR%\WinSxS\Manifests\ 資料夾中。 如果是私用組件，我們建議您將其資訊清單加入 DLL，做為 ID 等於 1 的資源。 您也可以將私用組件命名為和 DLL 相同的名稱。 如需詳細資訊，請參閱 <<c0> [ 關於私用組件](/windows/desktop/SbsCs/about-private-assemblies-)。  
  
 在執行時，Windows 會使用應用程式資訊清單中的組件資訊來搜尋及載入相對應的並存組件。 如果隔離之應用程式指定組件相依性，則作業系統會先在 %WINDIR%\WinSxS\ 資料夾原生組件快取中的共用組件之間搜尋這個組件。 如果找不到必要的組件，則作業系統會搜尋在應用程式目錄結構之資料夾內的私用組件。 如需詳細資訊，請參閱 <<c0> [ 組件搜尋序列](/windows/desktop/SbsCs/assembly-searching-sequence)。  
  
## <a name="changing-dependencies"></a>變更相依性  
 藉由修改應用程式部署之後，您可以變更並存的組件相依性[發行者組態檔](/windows/desktop/SbsCs/publisher-configuration-files)並[應用程式組態檔](/windows/desktop/SbsCs/application-configuration-files)。 發行者組態檔又稱為發行者原則檔，是一種 XML 檔案，會將應用程式和組件從使用一種並存組件版本全面重新導向為使用相同組件的另一個版本。 例如，當針對並存組件部署 Bug 修正或安全性修正，而且您想要將所有應用程式重新導向以使用修正版本時，您可以變更相依性。 應用程式組態檔是一種 XML 檔案，會將某特定應用程式從使用一種並存組件版本重新導向為使用相同組件的另一個版本。 您可以使用應用程式組態檔重新導向應用程式，以使用與發行者組態檔中所定義的版本不同的並存組件版本。 如需詳細資訊，請參閱[組態](/windows/desktop/SbsCs/configuration)。  
  
## <a name="visual-c-libraries"></a>Visual C++ 程式庫  
 在 Visual Studio 2005 和 Visual Studio 2008 中，ATL、MFC、CRT、Standard C++、OpenMP 和 MSDIA 等可轉散發程式庫都是以共用並存組件的形式部署至原生組件快取。 在目前的版本，可轉散發程式庫使用的是集中部署。 根據預設，使用 Visual C++ 建置的所有應用程式都是以最終二進位檔中內嵌的資訊清單建置而成，而資訊清單會描述這個二進位檔對於 Visual C++ 程式庫的相依性。 若要了解 Visual C++ 應用程式資訊清單的產生方式，請參閱 [Understanding Manifest Generation for C/C++ Programs](../build/understanding-manifest-generation-for-c-cpp-programs.md)。 靜態連結至其使用之程式庫或是使用本機部署的應用程式，並不需要資訊清單。 如需部署的詳細資訊，請參閱 [Deployment in Visual C++](../ide/deployment-in-visual-cpp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)