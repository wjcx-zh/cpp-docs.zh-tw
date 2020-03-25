---
title: 專案建置錯誤 PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: d02325504b04a13cd15dee0bd70891bf5a63b62e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192955"
---
# <a name="project-build-error-prj0009"></a>專案建置錯誤 PRJ0009

無法開啟組建記錄檔進行寫入。

**請確認檔案未被其他進程開啟，而且不受寫入保護。**

將 [**組建記錄**] 屬性設定為 **[是]** 並執行組建或重建C++之後，Visual 無法以獨佔模式開啟組建記錄檔。

開啟 [**選項**] 對話方塊（在 [**工具**] 功能表上按一下 [**選項**] [命令]），然後在 [**專案**] 資料夾中選取 [ **VC + + 組建**]，以檢查**組建記錄**設定。 組建檔案稱為 Buildlog.htm，並會寫入中繼目錄 $ （IntDir）。

此錯誤的可能原因：

- 您正在執行兩個視覺效果C++ ，並嘗試同時在兩者中建立相同專案的相同設定。

- 組建記錄檔會在鎖定檔案的進程中開啟。

- 使用者沒有建立檔案的許可權。

- 目前的使用者沒有 Buildlog.htm 檔案的寫入權限。
