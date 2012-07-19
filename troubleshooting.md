# Troubleshooting

======

more at [upgrade.md]

# Troubleshooting common mapping bugs with Castle


# Troubleshooting common mapping bugs with NHibernate

- "No ISessionFactory implementation associated with the given alias: nh.facility.default"
  https://gist.github.com/3137006
- public virtual string Name { get; private set; } 升级到nh3.x后mapping验证无法通过private
  add <item key="use_proxy_validator">false</item>

# Troubleshooting common mapping bugs with CodeSharp.*