---
title: /O 選項 (將程式碼最佳化)
description: MSVC/O 編譯器選項會指定要使用的編譯器優化。
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: 36ef582787a3ec2d7aee1e589c70b48712d9d552
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180873"
---
# <a name="o-options-optimize-code"></a>`/O` (優化程式碼的選項) 

這些 **`/O`** 選項可控制各種優化，協助您建立程式碼，以達到最大速度或最小大小。

- [`/O1`](o1-o2-minimize-size-maximize-speed.md)設定會產生最小大小程式代碼的優化組合。

- [`/O2`](o1-o2-minimize-size-maximize-speed.md)設定優化的組合，以優化程式碼的最大速度。

- [`/Ob`](ob-inline-function-expansion.md)控制內嵌函數展開。

- [`/Od`](od-disable-debug.md)停用優化，以加速編譯並簡化調試。

- [`/Og`](og-global-optimizations.md) (已淘汰) 會啟用全域優化。

- [`/Oi`](oi-generate-intrinsic-functions.md)產生適用于適當函式呼叫的內建函式。

- [`/Os`](os-ot-favor-small-code-favor-fast-code.md)告訴編譯器針對速度優化優化大小。

- [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) (預設設定) 會告訴編譯器偏好優化以取得大小優化的速度。

- [`/Ox`](ox-full-optimization.md)是一個組合選項，會選取數個優化並強調速度。 **`/Ox`** 是優化的嚴格子集 **`/O2`** 。

- [`/Oy`](oy-frame-pointer-omission.md)抑制在呼叫堆疊上建立框架指標，以加快函式呼叫的速度。

## <a name="remarks"></a>備註

您可以將多個 **`/O`** 選項結合成單一 option 語句。 例如，與 **`/Odi`** 相同 **`/Od /Oi`** 。 某些選項是互斥的，如果同時使用，則會造成編譯器錯誤。 如需詳細資訊，請參閱個別 **`/O`** 選項。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
