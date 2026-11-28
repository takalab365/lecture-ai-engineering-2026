# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前：glossary_search_glossary

- STEP 2 の [tool call]：glossary_search_glossary({'query': '3レベル'})

- STEP 3 の [tool call]：fetch_fetch({'url': 'https://modelcontextprotocol.io/'})

- STEP 4 の [tool call]：aws_aws___search_documentation({'topics': ['general'], 'search_phrase': 'Amazon S3 バージョニング 概要'})

aws_aws___search_documentation({'topics': ['general'], 'search_phrase': '"Versioning" "Amazon S3" what is'})

- 気づき・疑問：


## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：基礎
- やったこと：app/mcp_server.py にserver.tool()(tools.get_lecture_summary)を追記

- 結果：ツールが7個から8個に増え、「[glossary_get_lecture_summary]
    指定した回（1始まりの整数）の講義の要点を返す。
    
    「第3回では何を学ぶ？」のように、回の内容や関係を聞かれたときに使う。
    引数: {"lecture": {"title": "Lecture", "type": "integer"}}」がツールとして追加された

    [tool call]   glossary_get_lecture_summary({'lecture': 2})
    [usage] 入力 5,942 tokens / 出力 223 tokens / モデル応答 2 回
    uv run pytest -q → 21 passed

- 気づき・疑問：
    １行追加するだけで、簡単に呼び出せる
    修正したのは app/mcp_server.py だけで、エージェント側は修正していない。
    ツールが使えたのは、エージェントが起動するたびにツール一覧を問い合わせするから。