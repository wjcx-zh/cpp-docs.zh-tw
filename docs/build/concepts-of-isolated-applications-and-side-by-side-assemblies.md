---
title: 隔離應用程式和並存組件的概念
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
ms.openlocfilehash: ac354ed34bc3ab849eecf9256b447308f449abfe
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693564"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>隔離應用程式和並存組件的概念

如果某個應用程式的所有元件都是 [並存組件](/windows/desktop/SbsCs/isolated-applications) ，那麼就可以將這個應用程式視為 [隔離的應用程式](/windows/desktop/SbsCs/about-side-by-side-assemblies-)。 並存組件是資源的集合，是一組共同部署的 DLL、Windows 類別、COM 伺服器、類型程式庫或介面，可供應用程式在執行階段使用。 一般而言，並存組件是一至數個 DLL，

## <a name="shared-or-private"></a>共用或私用

並存組件可以是共用或私用組件。 在其資訊清單中指定對組件之相依性的多個應用程式，可使用[共用並存組件](https://msdn.microsoft.com/library/aa375996.aspx) 。 而同時間執行的不同應用程式，則可以共用並存組件的多個版本。 [私用組件](/windows/desktop/SbsCs/about-private-assemblies-) 是隨應用程式一同部署的組件，專供該應用程式使用。 私用組件會安裝在含有應用程式可執行檔的資料夾中，或是安裝在它的其中一個子資料夾中。

## <a name="manifests-and-search-order"></a>資訊清單和搜尋順序

[資訊清單](/windows/desktop/sbscs/manifests)會描述隔離的應用程式和並存組件。 資訊清單是 XML 文件，它可以是外部檔案，也可以內嵌於應用程式中或組件中以做為資源。 隔離之應用程式的資訊清單檔是用來管理共用之並存組件的名稱和版本 (應用程式在執行階段應該要繫結至這個組件)。 並存組件的資訊清單會指定並存組件的名稱、版本、資源和相依組件。 如果是共用並存組件，它的資訊清單會安裝在 %WINDIR%\WinSxS\Manifests\ 資料夾中。 如果是私用組件，我們建議您將其資訊清單加入 DLL，做為 ID 等於 1 的資源。 您也可以將私用組件命名為和 DLL 相同的名稱。 如需詳細資訊，請參閱 <<c0> [ 關於私用組件](/windows/desktop/SbsCs/about-private-assemblies-)。

在執行時，Windows 會使用應用程式資訊清單中的組件資訊來搜尋及載入相對應的並存組件。 如果隔離之應用程式指定組件相依性，則作業系統會先在 %WINDIR%\WinSxS\ 資料夾原生組件快取中的共用組件之間搜尋這個組件。 如果找不到必要的組件，則作業系統會搜尋在應用程式目錄結構之資料夾內的私用組件。 如需詳細資訊，請參閱 [Assembly Searching Sequence](/windows/desktop/SbsCs/assembly-searching-sequence)(組件搜尋順序)。

## <a name="changing-dependencies"></a>變更相依性

藉由修改 [發行者組態檔](/windows/desktop/SbsCs/publisher-configuration-files) 和 [應用程式組態檔](/windows/desktop/SbsCs/application-configuration-files)部署應用程式之後，您可以變更並存組件相依性。 發行者組態檔又稱為發行者原則檔，是一種 XML 檔案，會將應用程式和組件從使用一種並存組件版本全面重新導向為使用相同組件的另一個版本。 例如，當針對並存組件部署 Bug 修正或安全性修正，而且您想要將所有應用程式重新導向以使用修正版本時，您可以變更相依性。 應用程式組態檔是一種 XML 檔案，會將某特定應用程式從使用一種並存組件版本重新導向為使用相同組件的另一個版本。 您可以使用應用程式組態檔重新導向應用程式，以使用與發行者組態檔中所定義的版本不同的並存組件版本。 如需詳細資訊，請參閱 [Configuration](/windows/desktop/SbsCs/configuration)(組態)。

## <a name="visual-c-libraries"></a>Visual C++ 程式庫

在 Visual Studio 2005 和 Visual Studio 2008 中，ATL、MFC、CRT、Standard C++、OpenMP 和 MSDIA 等可轉散發程式庫都是以共用並存組件的形式部署至原生組件快取。 在目前的版本，可轉散發程式庫使用的是集中部署。 根據預設，使用 Visual C++ 建置的所有應用程式都是以最終二進位檔中內嵌的資訊清單建置而成，而資訊清單會描述這個二進位檔對於 Visual C++ 程式庫的相依性。 若要了解 Visual C++ 應用程式資訊清單的產生方式，請參閱 [Understanding Manifest Generation for C/C++ Programs](../build/understanding-manifest-generation-for-c-cpp-programs.md)。 靜態連結至其使用之程式庫或是使用本機部署的應用程式，並不需要資訊清單。 如需部署的詳細資訊，請參閱 [Deployment in Visual C++](../ide/deployment-in-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)