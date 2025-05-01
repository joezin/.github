![image](https://user-images.githubusercontent.com/6633808/160689302-3fe5e5d4-ba24-4525-8ed1-a8351ccbc0ef.png)

GitHub Community is built to support all GitHub users on their educational journey, via Discussions. It is a resource hub, learning portal, and inspiration station, all in one. Regardless of how big or small your challenge is, all resources and information will be accessible in a true open source fashion. 

### Quick Start

* [Discussions & Product Feedback](https://github.com/orgs/community/discussions)
* [Join Global Campus](https://education.github.com/benefits?type=student) 
* [GitHub Community Guidelines](https://docs.github.com/en/site-policy/github-terms/github-community-guidelines)
* [Student Developer Pack Application & FAQs](https://github.com/orgs/community/discussions/17814)

### Documentation

* [GitHub Terms of Service](https://docs.github.com/en/site-policy/github-terms/github-terms-of-service)
* [GitHub Community Forum Code of Conduct](https://docs.github.com/en/site-policy/github-terms/github-community-forum-code-of-conduct)

### Other Ways to Participate

* [GitHub Stars Program](https://stars.github.com/program/)
* [GitHub Campus Experts Program](https://education.github.com/experts)
* [GitHub Events](https://www.meetup.com/pro/github-virtual-meetup/)
* [GitHub Blog](https://github.blog/)
* [The ReadME Project & Podcast](https://github.com/readme)
* [GitHub YouTube Channel](https://www.youtube.com/github)

#### Quick note on 3rd party integrations
> _Due to an overwhelming number of suspicious requests from community members for 3rd party apps and integrations to this org, we've turned off "Allow integration requests from outside collaborators"._

#### Quick note on temporary interaction limits
In an effort to reduce spammy behavior, we are instituting temporary interaction limits to bar accounts less than 24hrs-old from participating in the `github.com/community` Discussions space. 
Accounts that are at least 24hrs old will be able to post and interact as normal.

If your account is less than 24hrs old and you have a question, please try using the Discussions search bar above to see if your question has already been asked or simply wait a day. We apologize if this causes any inconvenience.

If you'd like to learn more about implementing temporary interaction limits in your own orgs and repos, please read up on the official documentation [here](https://docs.github.com/en/communities/moderating-comments-and-conversations/limiting-interactions-in-your-organization).

# 检查权限
ls -la ~/.git-credentials

# 检查 Git 配置
git config --list | grep credential

# 检查凭证存储配置
git config --global credential.helper

# 检查凭证存储配置
secretservice

# 检查凭证文件
cat ~/.git-credentials

# 检查 Git 用户信息
git config --global user.name
git config --global user.email

# 测试凭证是否生效
git ls-remote https://github.com/dinhchow/.github.git

# 1. 完全清理所有凭证
echo "=== 清理所有凭证 ==="
git config --global --unset-all credential.helper
rm -f ~/.git-credentials
security delete-generic-password -a dinhchow -s github.com -l "GitHub" 2>/dev/null || echo "没有找到旧凭证"

# 2. 重新设置凭证管理
echo "=== 设置凭证管理 ==="
git config --global credential.helper osxkeychain

# 3. 强制要求重新认证
echo "=== 测试连接（将提示输入凭证）==="
git credential reject
protocol=https
host=github.com

# 4. 测试连接
echo "=== 尝试连接 GitHub ==="
git ls-remote https://github.com/dinhchow/.github.git

