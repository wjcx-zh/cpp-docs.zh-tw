---
title: 特性指引最佳化的環境變數
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195262"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>特性指引最佳化的環境變數

有三個環境變數會影響以 **/ltcg： PGI**建立之影像上的測試案例，以進行特性指引優化：

- **PogoSafeMode**指定是否要使用快速模式或安全模式進行應用程式分析。

- **VCPROFILE_ALLOC_SCALE**會新增額外的記憶體供 profiler 使用。

- **VCPROFILE_PATH**可讓您指定用於 .pgc 檔的資料夾。

**PogoSafeMode 和 VCPROFILE_ALLOC_SCALE 環境變數從 Visual Studio 2015 開始已淘汰。** 連結器選項[/GENPROFILE 或/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)和[/USEPROFILE](reference/useprofile.md)會指定與這些環境變數相同的連結器行為。

## <a name="pogosafemode"></a>PogoSafeMode

此環境變數已被取代。 請使用 **/GENPROFILE**或 **/FASTGENPROFILE**的**確切**或**NOEXACT**引數來控制此行為。

清除或設定**PogoSafeMode**環境變數，以指定是否要在 x86 系統上使用快速模式或安全模式進行應用程式分析。

特性指引優化（PGO）在分析階段期間有兩種可能的模式：*快速模式*和*安全模式*。 當分析處於快速模式時，它會使用**inc.** 指示來增加資料計數器。 **INC**指令的速度較快，但不是安全線程。 當分析處於安全模式時，它會使用**LOCK inc.** 指示來增加資料計數器。 **LOCK inc.** 指令具有與**inc.** 指示相同的功能，而且是安全線程，但是速度比**inc**指示慢。

根據預設，PGO 分析會以快速模式運作。 只有當您想要使用安全模式時，才需要**PogoSafeMode** 。

若要在安全模式中執行 PGO 分析，您必須使用環境變數**PogoSafeMode**或連結器切換 **/PogoSafeMode**（視系統而定）。 如果您是在 x64 電腦上執行程式碼剖析，就必須使用連結器參數。 如果您要在 x86 電腦上執行分析，您可以使用連結器參數，或在開始優化程式之前，將**PogoSafeMode**環境變數設定為任何值。

### <a name="pogosafemode-syntax"></a>PogoSafeMode 語法

> **設定 PogoSafeMode**[**=**_值_]

將**PogoSafeMode**設定為任何值，以啟用安全模式。 設定而不使用值來清除先前的值，並重新啟用快速模式。

## <a name="vcprofile_alloc_scale"></a>VCPROFILE_ALLOC_SCALE

此環境變數已被取代。 請使用 **/GENPROFILE**或 **/FASTGENPROFILE**的**MEMMIN**和**MEMMAX**引數來控制此行為。

修改**VCPROFILE_ALLOC_SCALE**環境變數，以變更配置用來保存設定檔資料的記憶體數量。 在罕見的情況下，在執行測試案例時，無法使用足夠的記憶體來支援收集分析資料。 在這些情況下，您可以藉由設定**VCPROFILE_ALLOC_SCALE**來增加記憶體數量。 如果您在測試回合期間收到錯誤訊息，指出您的記憶體不足，請將較大的值指派給**VCPROFILE_ALLOC_SCALE**，直到測試回合完成但沒有記憶體不足的錯誤為止。

### <a name="vcprofile_alloc_scale-syntax"></a>VCPROFILE_ALLOC_SCALE 語法

> **設定 VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value*參數是您想要用來執行測試案例之記憶體數量的縮放因數。  預設值是 1。 例如，此命令列會將比例因數設定為2：

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofile_path"></a>VCPROFILE_PATH

使用**VCPROFILE_PATH**環境變數來指定要建立 .pgc 檔案的目錄。 根據預設，會在與所分析之二進位檔相同的目錄中建立 .pgc 檔案。 不過，如果二進位檔的絕對路徑不存在，可能是當您在建立二進位的不同電腦上執行設定檔案例時，您可以將**VCPROFILE_PATH**設定為存在於目的電腦上的路徑。

### <a name="vcprofile_path-syntax"></a>VCPROFILE_PATH 語法

> **設定 VCPROFILE_PATH**[**=**_路徑_]

將*path*參數設定為要在其中加入 .pgc 檔案的目錄路徑。 例如，此命令列會將資料夾設定為 C:\profile：

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[/GENPROFILE 和/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
