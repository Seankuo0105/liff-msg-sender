import streamlit as st
from PIL import Image
import io

st.title("📐 圖片高寬調整器")

# 上傳圖片
uploaded_file = st.file_uploader("請上傳一張圖片", type=["png", "jpg", "jpeg", "webp"])

if uploaded_file:
    image = Image.open(uploaded_file)
    st.image(image, caption="原始圖片", use_column_width=True)

    # 輸入目標尺寸
    width = st.number_input("輸入寬度", min_value=1, value=image.width)
    height = st.number_input("輸入高度", min_value=1, value=image.height)

    # 調整圖片尺寸
    if st.button("調整尺寸"):
        resized_image = image.resize((width, height))
        st.image(resized_image, caption="調整後的圖片", use_column_width=True)

        # 將圖片轉為可下載的格式
        img_bytes = io.BytesIO()
        resized_image.save(img_bytes, format="PNG")
        st.download_button(
            label="下載調整後圖片",
            data=img_bytes.getvalue(),
            file_name="resized_image.png",
            mime="image/png"
        )

