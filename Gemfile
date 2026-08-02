source "https://rubygems.org"

# GitHub Pages가 지원하는 Jekyll 버전/플러그인 세트를 그대로 사용합니다.
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-seo-tag"
end

# Windows/JRuby 환경 호환용 (필요 없으면 무시해도 됩니다)
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw]
