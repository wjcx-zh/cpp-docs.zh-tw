---
title: C++標準程式庫標頭檔
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 807e65c69e55d8790b77a493e4ae1878aa740557
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305412"
---
# <a name="c-standard-library-header-files"></a>C++標準程式庫標頭檔

C++標準程式庫和延伸模組的標頭檔（依類別）。

## <a name="headers-by-category"></a>依類別的標頭

::: moniker range=">=vs-2017"

| 分類 | 標頭 |
| - | - |
| [演算法](../cpp/algorithms-modern-cpp.md) | [\<演算法 >](algorithm.md)， [\<b >](cstdlib.md)， [\<數值 >](numeric.md) |
| 不可部分完成的作業 |  [\<](atomic.md)不可部分完成 ><sup>11</sup> |
| C 程式庫包裝函式 | [\<cassert>](cassert.md)、[\<ccomplex>](ccomplex.md)<sup>11 a b</sup>、[\<cctype>](cctype.md)、[\<cerrno>](cerrno.md)、[\<cfenv>](cfenv.md)<sup>11</sup>、[\<cfloat>](cfloat.md)、[\<cinttypes>](cinttypes.md)<sup>11</sup>、[\<ciso646>](ciso646.md)<sup>b</sup>、[\<climits>](climits.md)、[\<clocale>](clocale.md)、[\<cmath>](cmath.md)、[\<csetjmp>](csetjmp.md)、[\<csignal>](csignal.md)、[\<cstdalign>](cstdalign.md)<sup>11 a b</sup>、[\<cstdarg>](cstdarg.md)、[\<cstdbool>](cstdbool.md)<sup>11 a b</sup>、[\<cstddef>](cstddef.md)、[\<cstdint>](cstdint.md)<sup>11</sup>、[\<cstdio>](cstdio.md)、[\<cstdlib>](cstdlib.md)、[\<cstring>](cstring.md)、[\<ctgmath>](ctgmath.md)<sup>11 a b</sup>、[\<ctime>](ctime.md)、[\<cuchar>](cuchar.md)<sup>11</sup>、[\<cwchar>](cwchar.md)、[\<cwctype>](cwctype.md) |
| 概念 | \<概念 ><sup>20</sup> |
| [容器](../cpp/containers-modern-cpp.md) | |
| 序列容器 | [\<陣列 >](array.md)<sup>11</sup>、 [\<deque >](deque.md)、 [\<forward_list >](forward-list.md)<sup>11</sup>、 [\<清單 >](list.md)、 [\<向量 >](vector.md) |
| 已排序的關聯容器| [\<map>](map.md)、[\<set>](set.md) |
| 未排序的關聯容器 | [\<unordered_map >](unordered-map.md)<sup>11</sup>、 [\<unordered_set >](unordered-set.md)<sup>11</sup> |
| 容器配接器 | [\<queue>](queue.md)、[\<stack>](stack.md) |
| 容器視圖 | \<範圍 ><sup>20</sup> |
| [錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert >](cassert.md)、 [\<例外狀況 >](exception.md)、 [\<stdexcept> >](stdexcept.md)、 [\<](system-error.md)system_error ><sup>11</sup> |
| 一般公用程式 | \<任何 ><sup>17</sup>、 [\<bitset >](bitset.md)、\<charconv ><sup>17</sup>、 [\<b >](cstdlib.md)、\<執行 ><sup>17</sup>、 [\<功能 >](functional.md)、 [\<記憶體 >](memory.md)、\<memory_resource ><sup>17</sup>、\<選擇性 ><sup>17</sup>、 [\<比率](ratio.md)><sup>11</sup>、 [\<scoped_allocator](scoped-allocator.md)><sup>11</sup>、 [\<元組 >](tuple.md)<sup>11</sup>， [\<type_traits >](type-traits.md)<sup>11</sup>、 [\<typeindex >](typeindex.md)<sup>11</sup>、 [\<utility >](utility.md)、\<variant ><sup>17</sup> |
| [I/o 和格式設定](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes >](cinttypes.md)<sup>11</sup>、 [\<cstdio> >](cstdio.md)、 [\<filesystem >](filesystem.md)<sup>17</sup>、\<[a m >](fstream.md)、 [\<p >](iomanip.md)、 [\<ios >](ios.md)、 [\<iosfwd >](iosfwd.md)、 [\<iostream >](iostream.md)、 [\<istream >](istream.md)、 [\<](ostream.md)ostream >、\<[sstream >](sstream.md)、 [\<streambuf >](streambuf.md)、 [\<strstream >](strstream.md)<sup>c</sup>，\<syncstream ><sup>20</sup> |
| 迭代器 | [\<iterator>](iterator.md) |
| 語言支援 | [\<t >](cfloat.md)、 [\<climits >](climits.md)、 [\<codecvt >](codecvt.md)<sup>11 a</sup>、\<比較 ><sup>20</sup>、\<合約 ><sup>20</sup>、\<協同程式 ><sup>20</sup>、 [\<csetjmp >](csetjmp.md)、 [\<csignal >](csignal.md)、\<cstdarg [>](cstdarg.md)、 [\<cstddef >、\<](cstddef.md) [cstdint >](cstdint.md)<sup>11</sup>、 [\<b >](cstdlib.md)、 [\<exception >](exception.md)、 [\<initializer_list >](initializer-list.md)<sup>11</sup>、 [\<限制 >](limits.md)、\<[新 >](new.md)、 [\<typeinfo >](typeinfo.md)、\<版本 ><sup>20</sup> |
| 當地語系化 | [\<clocale >](clocale.md)、 [\<codecvt >](codecvt.md)<sup>11 a</sup>、 [\<cvt/wbuffer >](cvt-wbuffer.md)、\<[cvt/wstring >](cvt-wstring.md)、 [\<地區設定 >](locale.md) |
| 數學和數值 | \<位 ><sup>20</sup>、 [\<cfenv >](cfenv.md)<sup>11</sup>、 [\<h >](cmath.md)、 [\<複雜 >](complex.md)、 [\<b >](cstdlib.md)、 [\<限制 >](limits.md)、 [\<數值 >](numeric.md)、 [\<隨機 >](random.md)<sup>11</sup>、 [\<比例 >](ratio.md)<sup>11</sup>、 [\<valarray >](valarray.md) |
| [記憶體管理](../cpp/smart-pointers-modern-cpp.md) | [\<配置器 >](allocators-header.md)、 [\<記憶體 >](memory.md)、\<memory_resource ><sup>17</sup>、 [\<new >](new.md)、 [\<scoped_allocator >](scoped-allocator.md)<sup>11</sup> |
| 多執行緒 | \<不可部分完成的[>](atomic.md)<sup>11</sup>、 [\<condition_variable >](condition-variable.md)<sup>11</sup>、 [\<未來 >](future.md)<sup>11</sup>、 [\<mutex >](mutex.md)<sup>11</sup>、 [\<shared_mutex](shared-mutex.md)><sup>14</sup>、 [\<執行緒 >](thread.md)<sup>11</sup> |
| 範圍 | \<範圍 ><sup>20</sup> |
| 規則運算式 | [\<RegEx >](regex.md)<sup>11</sup> |
| 字串和字元資料 | [\<cctype >](cctype.md)、 [\<b >](cstdlib.md)、 [\<cstring >](cstring.md)、 [\<cuchar >](cuchar.md)<sup>11</sup>、 [\<cwchar >](cwchar.md)、 [\<cwctype >](cwctype.md)、 [\<RegEx >](regex.md)<sup>11</sup>、 [\<string >](string.md)、 [\<string_view >](string-view.md)<sup>17</sup> |
| 時間 | [\<chrono >](chrono.md)<sup>11</sup>， [\<ctime >](ctime.md) |

<sup>11</sup>新增 c + + 11 標準。
c + + 14 standard 中加入了<sup>14</sup>個。
<sup>17</sup>加上 c + + 17 標準。
<sup>20</sup>在 Draft c + + 20 standard 中加入了20。
c + + 17 標準中<sup>的</sup>已被取代。
<sup>b</sup>已于 Draft c + + 20 standard 中移除。
<sup>c</sup> c + + 98 標準中已淘汰。

::: moniker-end

::: moniker range="vs-2015"

|分類|標頭|
|-|-|
|[演算法](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|C 程式庫包裝函式|[\<cassert>](cassert.md)、[\<cctype>](cctype.md)、[\<cerrno>](cerrno.md)、[\<cfenv>](cfenv.md)、[\<cfloat>](cfloat.md)、[\<cinttypes>](cinttypes.md)、[\<ciso646>](ciso646.md)、[\<climits>](climits.md)、[\<clocale>](clocale.md)、[\<cmath>](cmath.md)、[\<csetjmp>](csetjmp.md)、[\<csignal>](csignal.md)、[\<cstdarg>](cstdarg.md)、[\<cstdbool>](cstdbool.md)、[\<cstddef>](cstddef.md)、[\<cstdint>](cstdint.md)、[\<cstdio>](cstdio.md)、[\<cstdlib>](cstdlib.md)、[\<cstring>](cstring.md)、[\<ctgmath>](ctgmath.md)、[\<ctime>](ctime.md)、[\<cwchar>](cwchar.md)、[\<cwctype>](cwctype.md)|
|[容器](../cpp/containers-modern-cpp.md)||
|序列容器|[\<陣列 >](array.md)、 [\<deque >](deque.md)、 [\<forward_list >](forward-list.md)、 [\<清單 >](list.md)、 [\<向量 >](vector.md)|
|已排序的關聯容器| [\<map>](map.md)、[\<set>](set.md)|
|未排序的關聯容器|[\<unordered_map >](unordered-map.md)、 [\<unordered_set >](unordered-set.md)|
|介面卡容器|[\<queue>](queue.md)、[\<stack>](stack.md)|
|[錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<例外狀況 >](exception.md)， [\<stdexcept> >](stdexcept.md)， [\<system_error >](system-error.md)|
|[I/o 和格式設定](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md)、[\<fstream>](fstream.md)、[\<iomanip>](iomanip.md)、[\<ios>](ios.md)、[\<iosfwd>](iosfwd.md)、[\<iostream>](iostream.md)、[\<istream>](istream.md)、[\<ostream>](ostream.md)、[\<sstream>](sstream.md)、[\<streambuf>](streambuf.md)、[\<strstream>](strstream.md)|
|迭代器|[\<iterator>](iterator.md)|
|當地語系化|[\<codecvt>](codecvt.md)、[\<cvt/wbuffer>](cvt-wbuffer.md)、[\<cvt/wstring>](cvt-wstring.md)、[\<locale>](locale.md)|
|數學和數值|[\<complex>](complex.md)、[\<limits>](limits.md)、[\<numeric>](numeric.md)、[\<random>](random.md)、[\<ratio>](ratio.md)、[\<valarray>](valarray.md)|
|[記憶體管理](../cpp/smart-pointers-modern-cpp.md)|[\<配置器 >](allocators-header.md)、 [\<記憶體 >](memory.md)、 [\<new >](new.md)、 [\<scoped_allocator >](scoped-allocator.md)|
|多執行緒|[\<](atomic.md)不可部分完成的 >、 [\<condition_variable >](condition-variable.md)、 [\<未來 >](future.md)、 [\<mutex >](mutex.md)、 [\<shared_mutex](shared-mutex.md)>、 [\<執行緒 >](thread.md)|
|其他公用程式|[\<bitset >](bitset.md)、 [\<chrono >](chrono.md)、 [\<功能 >](functional.md)、 [\<initializer_list >](initializer-list.md)、 [\<元組 >](tuple.md)、 [\<type_traits](type-traits.md)>、 [\<typeinfo >](typeinfo.md)、 [\<typeindex >](typeindex.md)、 [\<公用程式 >](utility.md)|
|字串和字元資料|[\<RegEx >](regex.md)， [\<字串 >](string.md)， [\<string_view >](string-view.md)

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用C++程式庫標頭](using-cpp-library-headers.md)\
[C++標準程式庫](cpp-standard-library-reference.md)
