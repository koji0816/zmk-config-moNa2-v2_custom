# zmk-config-moNa2-v2_custom/CMakeLists.txt の最終修正案

zephyr_library()

set(PMW3610_MODULE_DIR "${ZEPHYR_BASE}/../zmk-pmw3610-driver")

# 修正1: インクルードパスの調整（/drivers/pmw3610/ を想定）
include_directories(${PMW3610_MODULE_DIR}/drivers/pmw3610)

# 修正2: ソースファイルのパスを調整
# パスを /drivers/pmw3610/pmw3610.c に変更
target_sources(app PRIVATE
    ${PMW3610_MODULE_DIR}/drivers/pmw3610/pmw3610.c
)
