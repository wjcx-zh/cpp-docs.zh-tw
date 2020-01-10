---
title: 移植協力廠商程式庫
ms.date: 10/29/2019
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: 89460af1ad0b356f4f5952141636a9f067131750
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627195"
---
# <a name="porting-third-party-libraries"></a>移植協力廠商程式庫

當您將專案從 Visual Studio 2013 或更早版本升級為目前的視覺C++效果時，您也必須升級專案所使用的任何程式庫，以便程式庫和您的專案是使用相同的編譯器版本和類別來建立。 如果您沒有程式庫原始程式碼的存取權，而且程式庫無法透過 vcpkg 取得，則您必須從程式庫廠商取得更新的二進位檔。 (如需詳細資訊，請參閱[潛在升級問題概觀](overview-of-potential-upgrade-issues-visual-cpp.md))。

將應用程式從 Visual Studio 2015 或 Visual Studio 2017 升級為 Visual Studio 2019 時，並不需要升級相依性，因為這三個版本所產生的程式碼與二進位檔相容。 如需詳細資訊，請參閱[ C++ Visual Studio 2015 和 Visual Studio 2019 之間的二進位相容性](binary-compat-2015-2017.md)。

## <a name="vcpkg-for-open-source-libraries"></a>適用于開放原始碼程式庫的 vcpkg

過去，尋找和升級協力廠商程式庫有時是非 trivial 工作。 為了讓您更輕鬆地取得和C++重建協力廠商開放原始碼程式庫C++ ，視覺效果小組已建立一個稱為**VC + + 封裝工具**或**vcpkg**的命令列工具。 Vcpkg 具有許多常見 C++ 開放原始碼程式庫的可搜尋目錄。 您可以直接從 vcpkg 命令列於目錄中安裝任何程式庫。 安裝程式庫時，vcpkg 會在電腦上建立目錄樹狀結構，並在此資料夾中新增 .h、.lib 和二進位檔。 您可以在編譯命令列中使用此資料夾，或使用 vcpkg 整合安裝命令將它整合到 Visual Studio 2015 或以上版本。 整合程式庫位置之後，Visual Studio 可以找到它，並將它新增至您建立的任何新專案。 若要使用程式庫，只要對其使用 `#include`，Visual Studio 就會自動將 .lib 路徑新增到專案設定，並將 dll 複製到解決方案資料夾。 如需詳細資訊，請參閱 [vcpkg：C++ 的套件管理員](../build/vcpkg.md)。

## <a name="reporting-issues"></a>回報問題

如果您的開放原始碼程式庫不存在於**vcpkg**目錄中，您可以在[GitHub](https://github.com/Microsoft/vcpkg/issues)儲存機制上開啟問題，其中的社區C++和視覺效果小組可以看到它，而且可能會建立此程式庫的埠檔案。

## <a name="see-also"></a>請參閱

[Visual C++ 移植和升級指南](visual-cpp-porting-and-upgrading-guide.md)
