# Troubleshooting

======

more at [upgrade.md]

# Troubleshooting common mapping bugs with Castle


# Troubleshooting common mapping bugs with NHibernate

- "No ISessionFactory implementation associated with the given alias: nh.facility.default"
  https://gist.github.com/3137006

- public virtual string Name { get; private set; } 升级到nh3.x后无法直接mapping private setter属性
  add <item key="use_proxy_validator">false</item>

- log4net 日志在azure上乱码
  add encoding="UTF-8"
  同时注意在azure上notepad直接查看log中文仍然乱码，改用其他文本编辑器查看

# Troubleshooting common mapping bugs with CodeSharp.*