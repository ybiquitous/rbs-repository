task default: [:test]

desc "Test all gems"
task :test do
  %w[
    retryable
  ].each do |gem|
    sh "rbs", "--repo=gems", "-r", gem, "--no-stdlib", "paths"
    sh "rbs", "--repo=gems", "-r", gem, "--no-stdlib", "list"

    ENV["BUNDLE_GEMFILE"] = "test/Gemfile"
    sh "bundle", "exec", "steep", "check", "--steepfile=test/#{gem}/Steepfile"
  end
end
