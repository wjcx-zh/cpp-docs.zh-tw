---
title: 了解 C/C++ 程式的資訊清單產生過程
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492517"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>了解 C/C++ 程式的資訊清單產生過程

[資訊清單](/windows/win32/sbscs/manifests)是 XML 檔, 可以是外部 xml 檔案, 或是內嵌在應用程式或元件內的資源。 [隔離應用程式](/windows/win32/SbsCs/isolated-applications)的資訊清單是用來管理共用並存元件的名稱和版本, 應用程式應該在執行時間進行系結。 並存元件的資訊清單會指定其名稱、版本、資源和其他元件的相依性。

有兩種方式可以建立隔離應用程式或並存元件的資訊清單。 首先, 元件的作者可以手動建立遵循規則和命名需求的資訊清單檔。 或者, 如果程式只相依于 Visual C++元件 (例如 CRT、MFC、ATL 或其他專案), 則連結器可以自動產生資訊清單。

視覺效果C++程式庫的標頭包含元件資訊, 而當程式庫包含在應用程式代碼中時, 連結器會使用此元件資訊來形成最後二進位檔的資訊清單。 連結器不會在二進位檔中內嵌資訊清單檔案, 而且只能將資訊清單產生為外部檔案。 將資訊清單當做外部檔案使用, 可能不適用於所有案例。 例如, 建議私用元件具有內嵌的資訊清單。 在使用 nmake 建立程式碼的命令列組建中, 可以使用資訊清單工具內嵌資訊清單;如需詳細資訊, 請參閱[在命令列產生資訊清單](manifest-generation-at-the-command-line.md)。 以 Visual Studio 建立時, 可以在 [**專案屬性**] 對話方塊中設定資訊清單工具的屬性, 以內嵌資訊清單。請參閱[Visual Studio 中的資訊清單產生](manifest-generation-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

[隔離應用程式和並存組件的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[建置 C/C++ 隔離應用程式和並存組件](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
