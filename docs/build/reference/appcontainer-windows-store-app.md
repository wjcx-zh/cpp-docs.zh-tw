---
title: /APPCONTAINER （UWP/Microsoft Store 應用程式）
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: f7ab8cf1ce034580953fdf1403264e8ef3d3ff09
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812404"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER （Microsoft Store 應用程式）

指定連結器是否建立必須在應用程式容器中執行的可執行檔映像。

## <a name="syntax"></a>語法

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>備註

/APPCONTAINER 預設為關閉。

這個選項修改可執行檔，以指出是否必須在 appcontainer 處理序隔離環境中執行應用程式。 必須在 appcontainer 環境中執行的應用程式，指定 /APPCONTAINER — 例如，通用 Windows 平台 (UWP) 或 Windows Phone 8.x 應用程式。 （此選項會自動設定 Visual Studio 中從範本建立的通用 Windows 應用程式時。）桌面應用程式中，指定 /appcontainer: no 或省略選項。

/APPCONTAINER 選項是在 Windows 8 中引進。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **命令列**屬性頁。

1. 在 **其他選項**，輸入`/APPCONTAINER`或`/APPCONTAINER:NO`。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
