# zmk-config-moNa2-v2_custom/CMakeLists.txt の最終修正案

zephyr_library()

set(PMW3610_MODULE_DIR "${ZEPHYR_BASE}/../zmk-pmw3610-driver")

# 修正1: インクルードパスを追加
# ヘッダーファイルが 'include' ディレクトリにあることを想定
include_directories(${PMW3610_MODULE_DIR}/include)

# 修正2: ソースファイルのパスを、モジュールルート直下のファイル名に変更 (これまでのパス指定ミスを避けるため)
# pmw3610.c がモジュールルートにあると仮定
target_sources(app PRIVATE
    ${PMW3610_MODULE_DIR}/pmw3610.c
)
