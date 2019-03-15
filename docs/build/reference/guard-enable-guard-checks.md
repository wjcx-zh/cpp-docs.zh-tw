---
title: /GUARD (啟用防護檢查)
ms.date: 11/04/2016
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
ms.openlocfilehash: e48921e57977cc7a1ca6a580fed78a6a2a960a02
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818410"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (啟用防護檢查)

指定在可執行映像中進行控制流程防護檢查的支援。

## <a name="syntax"></a>語法

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>備註

當指定 /GUARD:CF 時，連結器會修改 .dll 或 .exe 的標頭，以表示控制流程防護 (CFG) 執行階段檢查的支援。 連結器也會將所需的控制項流程目標位址資料加入標頭。 根據預設，會停用 /GUARD:CF。 可以使用 /GUARD:NO 將其明確停用。 若要有效，/guard: cf 也需要[/DYNAMICBASE （使用位址空間配置隨機載入）](dynamicbase-use-address-space-layout-randomization.md)連結器選項，預設為開啟。

藉由編譯原始程式碼時[/guard: cf](guard-enable-control-flow-guard.md)選項，編譯器就會會控制流程分析藉由檢查所有可能目標位址的間接呼叫。 編譯器會插入程式碼，在執行階段確認間接呼叫指令的目標位址位於已知目標位址的清單中。 支援 CFG 的作業系統會停止無法通過 CFG 執行階段檢查的程式。 這使得攻擊者更難使用資料損毀變更呼叫目標來執行惡意程式碼。

必須同時對編譯器和連結器指定 /GUARD:CF 選項，以建立已啟用 CFG 的可執行檔映像。 已編譯，但未使用 /GUARD:CF 連結的程式碼會產生執行階段檢查的成本，但是不會啟用 CFG 保護。 若要指定 /guard: cf 選項時`cl`編譯及連結在一個步驟中，編譯器的命令會將連結器旗標。 當**控制流程防護**屬性設定在 Visual Studio 中，/guard: cf 選項會傳遞至編譯器和連結器。 當有分開編譯目的檔或程式庫時，必須在明確指定選項`link`命令。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 依序展開**組態屬性**，**連結器**，**命令列**。

1. 在 **其他選項**，輸入`/GUARD:CF`。

## <a name="see-also"></a>另請參閱

[/guard (啟用控制流程防護)](guard-enable-control-flow-guard.md)<br/>
[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
