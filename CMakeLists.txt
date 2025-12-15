# zmk-config-moNa2-v2_custom/CMakeLists.txt の最終確定版

zephyr_library()

set(PMW3610_MODULE_DIR "${ZEPHYR_BASE}/../zmk-pmw3610-driver")

# 修正: インクルードパスとして 'src' ディレクトリとモジュールルートを追加
# ヘッダーファイル (pmw3610.h, pixart.h) が見つかるようにする
include_directories(${PMW3610_MODULE_DIR}/src)
# このモジュールのヘッダーがモジュールルートのinclude/ではなくsrc/にあるため、
# アプリケーションが他の場所から参照できるようにモジュールルートも追加
# include_directories(${PMW3610_MODULE_DIR}) # これは不要な可能性が高いが、念のため

# 確定: ソースファイル (pmw3610.c) をアプリケーションのビルドに直接追加
# これにより、リンカーエラーの原因となっていたシンボルが生成されます。
target_sources(app PRIVATE
    ${PMW3610_MODULE_DIR}/src/pmw3610.c
)
