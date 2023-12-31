缺点：不能点击 Dataframe 组件上方的排序按钮，否则会乱。

```python
import pandas as pd
import gradio as gr

# Creating a sample dataframe
df = pd.DataFrame(
    {
        "A": [14, 4, 5, 4, 1],
        "B": [5, 2, 54, 3, 2],
        "C": [20, 20, 7, 3, 8],
        "D": [14, 3, 6, 2, 6],
        "E": [23, 45, 64, 32, 23],
    }
)

# Displaying the styled dataframe in Gradio
with gr.Blocks() as demo:
    dataframe = gr.DataFrame(df, interactive=False)
    info = gr.Markdown(label="Information")

    # dataframe.select
    @dataframe.select(inputs=dataframe, outputs=[dataframe, info], show_progress=False)
    def func(df: pd.DataFrame, evt: gr.SelectData):
        row = evt.index[0]

        def highlight_cols(x):
            df = x.copy()
            df.loc[:, :] = ""
            df.loc[row, :] = "background-color:#ffffb3"
            return df

        s = df.style.apply(highlight_cols, axis=None)
        info = (
            f"Position: **({evt.index[0]}, {evt.index[1]})**\n\nValue: **{evt.value}**"
        )

        return s, info


demo.launch()

```

