---
title: /O 選項 (最佳化程式碼)
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: ffd3023120f1d930a24ccef6fa297594062322df
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816122"
---
# <a name="o-options-optimize-code"></a>/O 選項 (最佳化程式碼)

**/O**選項可控制各種最佳化，可協助您建立最快速度或最小的程式碼。

- [/ O1](o1-o2-minimize-size-maximize-speed.md)設定產生最小的程式碼的最佳化的組合。

- [/ O2](o1-o2-minimize-size-maximize-speed.md)設定最佳化程式碼的最大速度最佳化的組合。

- [/Ob](ob-inline-function-expansion.md)控制內嵌函式展開。

- [/Od](od-disable-debug.md)停用最佳化，以加速編譯，並簡化偵錯。

- [/Og](og-global-optimizations.md)啟用全域最佳化。

- [/Oi](oi-generate-intrinsic-functions.md)會產生適當的函式呼叫的內建函式。

- [/Os](os-ot-favor-small-code-favor-fast-code.md)會指示編譯器大小最佳化優先於速度最佳化。

- [/Ot](os-ot-favor-small-code-favor-fast-code.md) （預設值） 會指示編譯器速度最佳化優先於大小最佳化。

- [/Ox](ox-full-optimization.md)是組合的選項，選取數個時應著重速度最佳化。 它是嚴格子集 **/o2**最佳化。

- [/Oy](oy-frame-pointer-omission.md)隱藏框架指標更快的函式呼叫的呼叫堆疊上的建立。

## <a name="remarks"></a>備註

您可以結合多個 **/O**成單一的選項陳述式的選項。 例如， **/Odi**等同於 **/Od /Oi**。 某些選項互斥，而且如果一起使用，會造成編譯器錯誤。 請參閱個別 **/O**選項的詳細資訊。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
