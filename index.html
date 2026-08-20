import React, { useState, useEffect } from 'react';
import { BookOpen, Plus, Trash2, Search, Bookmark, ExternalLink, ChevronDown, ChevronUp, Lock } from 'lucide-react';

// ★お好みのパスワードに変更してください
const CORRECT_PASSWORD = '3010';

export default function App() {
  // パスワード認証状態
  const [isAuthenticated, setIsAuthenticated] = useState(() => {
    return sessionStorage.getItem('manga_log_auth') === 'true';
  });
  const [passwordInput, setPasswordInput] = useState('');
  const [passError, setPassError] = useState(false);

  // データ管理
  const [works, setWorks] = useState(() => {
    const saved = localStorage.getItem('manga_scene_works');
    return saved ? JSON.parse(saved) : [
      {
        id: 1,
        title: '葬送のフリーレン',
        author: '山田鐘人 / アベツカサ',
        image: '',
        site: 'サンデーうぇぶり',
        tags: ['ファンタジー', 'ドラマ'],
        memo: '旅の過程での人間模様が美しい',
        scenes: [
          {
            id: 101,
            chapter: '第1話',
            page: '12p',
            memo: 'ヒンメルの葬儀でのフリーレンの涙。「なんでもっと知ろうとしなかったんだろう」',
            tags: ['名言', '感動']
          }
        ]
      }
    ];
  });

  const [searchWord, setSearchWord] = useState('');
  const [selectedTag, setSelectedTag] = useState('');
  const [selectedSite, setSelectedSite] = useState('');

  // 各作品の開閉状態（デフォルトはすべて閉じ）
  const [expandedMap, setExpandedMap] = useState({});

  // 新規作品の入力用
  const [newTitle, setNewTitle] = useState('');
  const [newAuthor, setNewAuthor] = useState('');
  const [newImage, setNewImage] = useState('');
  const [newSite, setNewSite] = useState('');
  const [newWorkTags, setNewWorkTags] = useState('');
  const [newWorkMemo, setNewWorkMemo] = useState('');

  // シーン追加の入力用（作品IDごとに管理）
  const [sceneInputs, setSceneInputs] = useState({});

  useEffect(() => {
    localStorage.setItem('manga_scene_works', JSON.stringify(works));
  }, [works]);

  // パスワード確認処理
  const handleLogin = (e) => {
    e.preventDefault();
    if (passwordInput === CORRECT_PASSWORD) {
      setIsAuthenticated(true);
      sessionStorage.setItem('manga_log_auth', 'true');
      setPassError(false);
    } else {
      setPassError(true);
    }
  };

  // 作品追加
  const addWork = (e) => {
    e.preventDefault();
    if (!newTitle.trim()) return;
    const newId = Date.now();
    const item = {
      id: newId,
      title: newTitle,
      author: newAuthor,
      image: newImage,
      site: newSite,
      tags: newWorkTags.split(',').map(t => t.trim()).filter(Boolean),
      memo: newWorkMemo,
      scenes: []
    };
    setWorks([item, ...works]);
    // 新規追加した作品は開いた状態にする
    setExpandedMap(prev => ({ ...prev, [newId]: true }));
    setNewTitle(''); setNewAuthor(''); setNewImage(''); setNewSite(''); setNewWorkTags(''); setNewWorkMemo('');
  };

  // 作品削除
  const deleteWork = (id, e) => {
    e.stopPropagation(); // クリックイベントの伝播を防止
    if (window.confirm('この作品と登録されたシーンをすべて削除しますか？')) {
      setWorks(works.filter(w => w.id !== id));
    }
  };

  // 手動での開閉切り替え
  const toggleExpand = (id) => {
    setExpandedMap(prev => ({ ...prev, [id]: !prev[id] }));
  };

  // シーン追加
  const addScene = (workId) => {
    const input = sceneInputs[workId] || {};
    if (!input.memo?.trim()) return;

    const newScene = {
      id: Date.now(),
      chapter: input.chapter || '',
      page: input.page || '',
      memo: input.memo,
      tags: input.tags ? input.tags.split(',').map(t => t.trim()).filter(Boolean) : []
    };

    setWorks(works.map(w => {
      if (w.id === workId) {
        return { ...w, scenes: [...w.scenes, newScene] };
      }
      return w;
    }));

    setSceneInputs({ ...sceneInputs, [workId]: { chapter: '', page: '', memo: '', tags: '' } });
  };

  // シーン削除
  const deleteScene = (workId, sceneId) => {
    setWorks(works.map(w => {
      if (w.id === workId) {
        return { ...w, scenes: w.scenes.filter(s => s.id !== sceneId) };
      }
      return w;
    }));
  };

  // 入力変更ハンドラ
  const handleSceneInputChange = (workId, field, value) => {
    setSceneInputs({
      ...sceneInputs,
      [workId]: { ...(sceneInputs[workId] || {}), [field]: value }
    });
  };

  // タグ・サイトの一覧抽出
  const allSites = Array.from(new Set(works.map(w => w.site).filter(Boolean)));
  const allTags = Array.from(new Set([
    ...works.flatMap(w => w.tags),
    ...works.flatMap(w => w.scenes.flatMap(s => s.tags))
  ]));

  // 検索条件が適用されているかの判定
  const isSearching = searchWord !== '' || selectedTag !== '' || selectedSite !== '';

  // フィルタリング処理
  const filteredWorks = works.filter(w => {
    const matchWord = searchWord === '' || 
      w.title.toLowerCase().includes(searchWord.toLowerCase()) ||
      w.author.toLowerCase().includes(searchWord.toLowerCase()) ||
      w.memo.toLowerCase().includes(searchWord.toLowerCase()) ||
      w.scenes.some(s => s.memo.toLowerCase().includes(searchWord.toLowerCase()));

    const matchSite = selectedSite === '' || w.site === selectedSite;

    const matchTag = selectedTag === '' || 
      w.tags.includes(selectedTag) ||
      w.scenes.some(s => s.tags.includes(selectedTag));

    return matchWord && matchSite && matchTag;
  });

  // 未ログイン時のパスワードロック画面
  if (!isAuthenticated) {
    return (
      <div style={{ display: 'flex', justifyContent: 'center', alignItems: 'center', minHeight: '100vh', backgroundColor: '#f8f9fa', fontFamily: 'sans-serif' }}>
        <form onSubmit={handleLogin} style={{ backgroundColor: '#fff', padding: '30px', borderRadius: '12px', boxShadow: '0 4px 12px rgba(0,0,0,0.1)', textAlign: 'center', width: '300px' }}>
          <Lock size={40} color="#007bff" style={{ marginBottom: '10px' }} />
          <h2 style={{ fontSize: '20px', margin: '0 0 20px 0' }}>推しシーンログ</h2>
          <input
            type="password"
            placeholder="パスワードを入力"
            value={passwordInput}
            onChange={(e) => setPasswordInput(e.target.value)}
            style={{ width: '100%', padding: '10px', borderRadius: '6px', border: '1px solid #ccc', marginBottom: '10px', boxSizing: 'border-box' }}
          />
          {passError && <p style={{ color: '#dc3545', fontSize: '12px', margin: '0 0 10px 0' }}>パスワードが違います</p>}
          <button type="submit" style={{ width: '100%', padding: '10px', backgroundColor: '#007bff', color: '#fff', border: 'none', borderRadius: '6px', cursor: 'pointer', fontWeight: 'bold' }}>
            解除する
          </button>
        </form>
      </div>
    );
  }

  // ログイン後のメイン画面
  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px', fontFamily: 'sans-serif', color: '#333', backgroundColor: '#f8f9fa', minHeight: '100vh' }}>
      <h1 style={{ display: 'flex', alignItems: 'center', gap: '10px', fontSize: '24px', color: '#1a1a1a' }}>
        <BookOpen color="#007bff" /> 推しシーンログ
      </h1>

      {/* 検索・フィルターエリア */}
      <div style={{ backgroundColor: '#fff', padding: '15px', borderRadius: '8px', boxShadow: '0 2px 4px rgba(0,0,0,0.05)', marginBottom: '20px' }}>
        <div style={{ display: 'flex', gap: '10px', marginBottom: '10px', flexWrap: 'wrap' }}>
          <div style={{ display: 'flex', alignItems: 'center', gap: '5px', flex: 1, minWidth: '200px', border: '1px solid #ccc', borderRadius: '4px', padding: '0 8px' }}>
            <Search size={16} color="#666" />
            <input
              type="text"
              placeholder="フリーワード検索（タイトル・キャラ・メモなど）"
              value={searchWord}
              onChange={e => setSearchWord(e.target.value)}
              style={{ border: 'none', outline: 'none', padding: '8px', width: '100%' }}
            />
          </div>

          <select value={selectedSite} onChange={e => setSelectedSite(e.target.value)} style={{ padding: '8px', borderRadius: '4px', border: '1px solid #ccc' }}>
            <option value="">すべての掲載サイト</option>
            {allSites.map(s => <option key={s} value={s}>{s}</option>)}
          </select>

          <select value={selectedTag} onChange={e => setSelectedTag(e.target.value)} style={{ padding: '8px', borderRadius: '4px', border: '1px solid #ccc' }}>
            <option value="">すべてのタグ</option>
            {allTags.map(t => <option key={t} value={t}>{t}</option>)}
          </select>
        </div>
      </div>

      {/* 作品追加フォーム */}
      <details style={{ backgroundColor: '#fff', padding: '15px', borderRadius: '8px', boxShadow: '0 2px 4px rgba(0,0,0,0.05)', marginBottom: '20px' }}>
        <summary style={{ fontWeight: 'bold', cursor: 'pointer', color: '#007bff' }}>＋ 新しい作品を登録する</summary>
        <form onSubmit={addWork} style={{ display: 'flex', flexDirection: 'column', gap: '10px', marginTop: '15px' }}>
          <div style={{ display: 'flex', gap: '10px' }}>
            <input type="text" placeholder="作品タイトル（必須）" value={newTitle} onChange={e => setNewTitle(e.target.value)} style={{ flex: 2, padding: '8px', borderRadius: '4px', border: '1px solid #ccc' }} />
            <input type="text" placeholder="著者名" value={newAuthor} onChange={e => setNewAuthor(e.target.value)} style={{ flex: 1, padding: '8px', borderRadius: '4px', border: '1px solid #ccc' }} />
          </div>
          <div style={{ display: 'flex', gap: '10px' }}>
            <input type="text" placeholder="掲載サイト（例：ピッコマ、LINEマンガ）" value={newSite} onChange={e => setNewSite(e.target.value)} style={{ flex: 1, padding: '8px', borderRadius: '4px', border: '1px solid #ccc' }} />
            <input type="text" placeholder="作品タグ（カンマ区切り：スカッとする, 恋愛）" value={newWorkTags} onChange={e => setNewWorkTags(e.target.value)} style={{ flex: 1, padding: '8px', borderRadius: '4px', border: '1px solid #ccc' }} />
          </div>
          <input type="text" placeholder="画像URL（任意）" value={newImage} onChange={e => setNewImage(e.target.value)} style={{ padding: '8px', borderRadius: '4px', border: '1px solid #ccc' }} />
          <textarea placeholder="作品全体のメモ" value={newWorkMemo} onChange={e => setNewWorkMemo(e.target.value)} style={{ padding: '8px', borderRadius: '4px', border: '1px solid #ccc', height: '60px' }} />
          <button type="submit" style={{ padding: '10px', backgroundColor: '#007bff', color: '#fff', border: 'none', borderRadius: '4px', cursor: 'pointer', fontWeight: 'bold' }}>作品を保存</button>
        </form>
      </details>

      {/* 作品一覧 */}
      <div style={{ display: 'flex', flexDirection: 'column', gap: '15px' }}>
        {filteredWorks.map(work => {
          // 検索実行時は強制オープン、それ以外は個別状態（デフォルト閉じ）
          const isOpen = isSearching ? true : !!expandedMap[work.id];

          return (
            <div key={work.id} style={{ backgroundColor: '#fff', borderRadius: '8px', boxShadow: '0 2px 4px rgba(0,0,0,0.05)', overflow: 'hidden' }}>
              
              {/* 親データ：作品ヘッダー（クリックで開閉） */}
              <div 
                onClick={() => toggleExpand(work.id)} 
                style={{ padding: '15px', display: 'flex', gap: '15px', borderBottom: isOpen ? '1px solid #eee' : 'none', cursor: 'pointer', userSelect: 'none' }}
              >
                {work.image ? (
                  <img src={work.image} alt={work.title} style={{ width: '60px', height: '80px', objectFit: 'cover', borderRadius: '4px' }} />
                ) : (
                  <div style={{ width: '60px', height: '80px', backgroundColor: '#e9ecef', borderRadius: '4px', display: 'flex', alignItems: 'center', justifyContent: 'center' }}>
                    <BookOpen color="#adb5bd" />
                  </div>
                )}

                <div style={{ flex: 1 }}>
                  <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'flex-start' }}>
                    <div>
                      <h2 style={{ margin: '0 0 5px 0', fontSize: '18px', color: '#007bff' }}>{work.title}</h2>
                      {work.author && <span style={{ fontSize: '13px', color: '#666', marginRight: '10px' }}>{work.author}</span>}
                      {work.site && <span style={{ fontSize: '12px', backgroundColor: '#e7f5ff', color: '#1c7ed6', padding: '2px 6px', borderRadius: '4px' }}><ExternalLink size={10} /> {work.site}</span>}
                    </div>
                    <div style={{ display: 'flex', alignItems: 'center', gap: '5px' }}>
                      <span style={{ fontSize: '12px', color: '#888', marginRight: '5px' }}>
                        推しシーン: {work.scenes.length}件
                      </span>
                      {isOpen ? <ChevronUp size={20} color="#666" /> : <ChevronDown size={20} color="#666" />}
                      <button onClick={(e) => deleteWork(work.id, e)} style={{ border: 'none', background: 'none', cursor: 'pointer', padding: '4px', color: '#dc3545', marginLeft: '5px' }}>
                        <Trash2 size={18} />
                      </button>
                    </div>
                  </div>

                  {work.memo && <p style={{ fontSize: '13px', color: '#555', margin: '8px 0 5px 0' }}>{work.memo}</p>}

                  {work.tags.length > 0 && (
                    <div style={{ display: 'flex', gap: '5px', flexWrap: 'wrap', marginTop: '5px' }}>
                      {work.tags.map((t, idx) => (
                        <span key={idx} style={{ fontSize: '11px', backgroundColor: '#f1f3f5', color: '#495057', padding: '2px 6px', borderRadius: '12px' }}>#{t}</span>
                      ))}
                    </div>
                  )}
                </div>
              </div>

              {/* 子データ：推しシーン一覧 & 追加フォーム（開いている時だけ表示） */}
              {isOpen && (
                <div style={{ backgroundColor: '#fcfcfc', padding: '15px' }}>
                  <h3 style={{ fontSize: '14px', margin: '0 0 10px 0', color: '#495057', display: 'flex', alignItems: 'center', gap: '5px' }}>
                    <Bookmark size={14} /> 推しシーン ({work.scenes.length})
                  </h3>

                  {/* シーン一覧 */}
                  <div style={{ display: 'flex', flexDirection: 'column', gap: '8px', marginBottom: '15px' }}>
                    {work.scenes.map(scene => (
                      <div key={scene.id} style={{ backgroundColor: '#fff', border: '1px solid #e9ecef', padding: '10px', borderRadius: '6px', position: 'relative' }}>
                        <div style={{ display: 'flex', justifyContent: 'space-between', marginBottom: '4px' }}>
                          <span style={{ fontSize: '12px', fontWeight: 'bold', color: '#007bff' }}>
                            {scene.chapter} {scene.page && `(${scene.page})`}
                          </span>
                          <button onClick={() => deleteScene(work.id, scene.id)} style={{ border: 'none', background: 'none', cursor: 'pointer', color: '#adb5bd', padding: 0 }}>
                            <Trash2 size={14} />
                          </button>
                        </div>
                        <p style={{ margin: '0 0 6px 0', fontSize: '13px', whiteSpace: 'pre-wrap' }}>{scene.memo}</p>
                        {scene.tags.length > 0 && (
                          <div style={{ display: 'flex', gap: '4px', flexWrap: 'wrap' }}>
                            {scene.tags.map((st, idx) => (
                              <span key={idx} style={{ fontSize: '10px', color: '#1098ad', backgroundColor: '#e6fcff', padding: '1px 5px', borderRadius: '4px' }}>#{st}</span>
                            ))}
                          </div>
                        )}
                      </div>
                    ))}
                  </div>

                  {/* シーン追加インラインフォーム */}
                  <div style={{ borderTop: '1px dashed #dee2e6', paddingTop: '10px' }}>
                    <div style={{ display: 'flex', gap: '5px', marginBottom: '5px' }}>
                      <input
                        type="text"
                        placeholder="話数・巻数（例: 第12話）"
                        value={sceneInputs[work.id]?.chapter || ''}
                        onChange={e => handleSceneInputChange(work.id, 'chapter', e.target.value)}
                        style={{ flex: 1, padding: '6px', fontSize: '12px', borderRadius: '4px', border: '1px solid #ccc' }}
                      />
                      <input
                        type="text"
                        placeholder="ページ（任意）"
                        value={sceneInputs[work.id]?.page || ''}
                        onChange={e => handleSceneInputChange(work.id, 'page', e.target.value)}
                        style={{ width: '80px', padding: '6px', fontSize: '12px', borderRadius: '4px', border: '1px solid #ccc' }}
                      />
                    </div>
                    <input
                      type="text"
                      placeholder="シーンタグ（カンマ区切り：名言, 伏線回収）"
                      value={sceneInputs[work.id]?.tags || ''}
                      onChange={e => handleSceneInputChange(work.id, 'tags', e.target.value)}
                      style={{ width: '100%', padding: '6px', fontSize: '12px', borderRadius: '4px', border: '1px solid #ccc', marginBottom: '5px', boxSizing: 'border-box' }}
                    />
                    <div style={{ display: 'flex', gap: '5px' }}>
                      <input
                        type="text"
                        placeholder="推しシーン・メモ（必須）"
                        value={sceneInputs[work.id]?.memo || ''}
                        onChange={e => handleSceneInputChange(work.id, 'memo', e.target.value)}
                        style={{ flex: 1, padding: '6px', fontSize: '12px', borderRadius: '4px', border: '1px solid #ccc' }}
                      />
                      <button
                        onClick={() => addScene(work.id)}
                        style={{ padding: '6px 12px', backgroundColor: '#28a745', color: '#fff', border: 'none', borderRadius: '4px', fontSize: '12px', cursor: 'pointer', fontWeight: 'bold' }}
                      >
                        シーン追加
                      </button>
                    </div>
                  </div>

                </div>
              )}
            </div>
          );
        })}
      </div>
    </div>
  );
}
