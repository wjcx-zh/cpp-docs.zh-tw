---
title: 偵錯提供者
ms.date: 10/29/2018
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: f80ce5dc82dd2baeefe3410a488a5fefda0e9bf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211090"
---
# <a name="debugging-your-provider"></a>偵錯提供者

有兩種方式可讓您用來對提供者進行偵錯工具：

- 因為提供者是在程式中建立的，所以您可以使用 OLE DB 取用者範本建立一些取用者程式碼，並以一般方式逐步執行至提供者。

- 您可以使用視覺效果C++隨附的各種公用程式。

## <a name="to-use-debugging"></a>若要使用調試

1. 開啟提供者專案。

1. 在 [**專案**] 功能表上，按一下 [**屬性**]。

1. 在 [**屬性頁**] 對話方塊中，按一下 [**調試**] 索引標籤。

1. 視需要選取 [選項]，然後按一下 **[確定]** 。

1. 設定中斷點，然後依照平常的方式進行 debug。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)
